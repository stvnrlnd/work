Add ABHP attendees to the current meeting note.

The ABHP fixed attendee group is: Shawn K., Andre R., Craig B., Steven R., Brian M., Taylor S.

1. Ask the user for the path to the meeting note they want to update (or check if they mentioned it in context).

2. Read the file.

3. Update the frontmatter:
   - Set `area: abhp`
   - Set `attendees` to the ABHP list

4. In the `## Since Last We Met` section, replace the generic `-` placeholder with individual subsections:
   ```
   ### Shawn K.
   -
   ### Andre R.
   -
   ### Craig B.
   -
   ### Steven R.
   -
   ### Brian M.
   -
   ### Taylor S.
   -
   ```

5. In the `## Ratings` section, replace the generic `-` placeholder with:
   ```
   - Shawn K.:
   - Andre R.:
   - Craig B.:
   - Brian M.:
   - Taylor S.:
   - Steven R.:
   ```

6. Confirm the changes were made and show the updated frontmatter.
