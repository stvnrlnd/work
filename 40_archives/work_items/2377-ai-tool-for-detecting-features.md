---
title: 2377-ai-tool-for-detecting-features
type: work-item
item_type: task
project: houseplans.net
status: in-review
created: 2026-04-14
updated:
due: 2026-04-07
url: https://trello.com/c/F6tMplva/2377-ai-tool-for-detecting-features
assignee: Shawn K.
---

# 2377-ai-tool-for-detecting-features

## Description

REVISION:

Installation script

Guards for dev servers and database backups to prevent API calls

Progress page so users can see how long they might have to wait and when the process is done

### Details:

Run the Celery app from the tools/ai-task-runner directory. The normal flow is: create a Python virtual environment, install dependencies, create a real .env file, then start with ./run_tool.sh up. The runner polls every 10 seconds and enqueues pending/error plans; the worker processes them and writes results back to plan_feature_analysis.

Key points:

- Go to: /data/development/houseplans.net/tools/ai-task-runner
    
- Create virtual env + install:  
    python -m venv .venv  
    source .venv/bin/activate  
    pip install -r requirements.txt  
    Install redis and make sure its service is running
    
- Create a proper .env (copy then edit):  
    cp .env.example .env  
    Minimum required values:  
    GEMINI_API_KEY="YOUR_REAL_KEY"  
    REDIS_URL="redis://localhost:6379/0"  
    MYSQL_URL="mysql+pymysql://user:pass@127.0.0.1:3306/yourdb?charset=utf8mb4"  
    Additional .env parameters:  
    GEMINI_MODEL="gemini-3-flash-preview"  
    GEMINI_THINKING_LEVEL="low" -- This really shouldn't be modified because it impacts the speed/accuracy heavily  
    GEMINI_RPM=20 -- The default set in the code are already fairly well optimized  
    MAX_RETRIES=10  
    TASK_SOFT_TIME_LIMIT=240  
    TASK_TIME_LIMIT=300  
    AUTO_ENQUEUE_BATCH=10  
    ENQUEUE_BATCH=8
    
- Start everything:  
    ./run_tool.sh up
    

We want to build an AI tool that analyzes plan images and identifies features from a predefined list.

The list should be stored in a separate database table, and identify the image types that the feature might be found in (for customizing prompts).

The results should be stored in a database table that records which image the feature was seen in.

After all images for a plan are scanned, the entire collection of matching features should be listed in the plan administration area for review.

We will also want to include a plan scanning cron that runs against plans one at a time on a scheduled interval, starting with the most popular plans from our plan rank algorithm. Keeping track of which images have been scanned will also be useful when a scan is interrupted or needs to be restarted (or if new images are added).

Here is the list of features: [https://docs.google.com/document/d/1UjehRUckKjStG_lreR2z2mO1GMXUIK4dRDUvzKmuOjg/edit?usp=sharing](https://docs.google.com/document/d/1UjehRUckKjStG_lreR2z2mO1GMXUIK4dRDUvzKmuOjg/edit?usp=sharing)

---

Context: Previous discussion was in this card: [https://trello.com/c/pXzurUoc](https://trello.com/c/pXzurUoc)`

## Notes

