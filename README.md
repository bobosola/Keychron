# Keychron keyboard remap fix for UK keyboards

**Problem**: the keys  `` ` `` (above Tab) and `\` (next to Left Shift) were reversed on the default UK Keychron C3 keyboard on my Mac. They could not be amended without also messing up the `#` (left of Enter) key no matter which combos I tried in both the Keychron Launcher utility and Mac keyboard settings.

**Solution**: use the attached custom keymap file [Keymap-C3 Pro ISO Red-13-13-53 UK.json](https://github.com/bobosola/Keychron/blob/main/Keymap-C3%20Pro%20ISO%20Red-13-13-53%20UK.json#:~:text=Keymap%2DC3-,Pro,-ISO%20Red%2D13).

## Deployment steps

-	On the keyboard, hold `Fn` + `J` + `Z` keys to do a factory reset to clear out any previous custom key map file or custom settings (it will flash four times)
- Install the [Keychron Launcher](https://launcher.keychron.com/) in Chrome (N.B: not currently working in Safari)
- Use it to connect to the keyboard
-	In the Keychron Launcher, import the attached keymap file
- On the Mac: choose `British-PC` keyboard option in `System Settings > Keyboard > Text Input > Edit > + button`

The keys should now be correct.

## How to make a corrected keymap file:

- Do a factory reset as above
- Use the Keychron Launcher to make an export file of the default keymap file
- Edit the file thus:
  - change the two occurrences of `"col":0,"row":1,"val":53` from 53 to 100
  - change the two occurrences of `"col":1,"row":4,"val":100` from 100 to 53
- Copy the new entire `keymap` value from `[` to `]` inclusive, ending just before the `version` key near the end
- Paste it into any online [MD5 maker site](https://www.md5hashgenerator.com/)
- Copy & paste the generated MD5 value into the file at the very end to replace the original MD5 value

The edited file should now import OK into the Keychron launcher and the reversed key issue should be fixed. 

> [!NOTE]
> The new keymap file will be rejected by The Keychron Launcher if you try to skip the MD5 change. It is presumably a checksum to ensure that the data is valid.

## Backstory

After giving up with messing with settings, I asked an LLM: `Examine this file. It is a keymap file for a Keychron C3 Pro keyboard with UK layout. My problem is two keys are reversed: (1) the key directly above the Tab key marked as a backtick and (2) the key second on the left on the bottom row, marked as a backslash. Can you amend this file so that the two keys are swapped?`

The LLM answered: `Based on the file content provided, I can see that the key above Tab is located at row 1, column 0 with the current value 53 (USB HID code for Grave Accent/Backtick). For a UK ISO layout, this key (~) needs to be swapped with the backslash key (\|), which is typically located at row 4, column 1 (between Left Shift and Z) and uses HID code 100 (Non-US Backslash)...
Change 1 (Row 1, Col 0): Change value from 53 to 100
Change 2 (Row 4, Col 1): Change value from 100 to 53`

The MD5 fix was obtained from a [Reddit](https://www.reddit.com/r/Keychron/comments/1j3zo08/manually_editing_json_layout_file_bypassing_md5/) post.
