What it does: It checks a survey point file for problems that would break an import or point to bad field data, then gives you a cleaned version. Everything runs in your browser, so your file never gets uploaded anywhere.

Step by step
Get your data in. Drag a file into the dashed box, tap browse to pick one, or paste your points straight into the big text area. A loaded file validates automatically.
Check the column order. Leave it on Auto-detect unless you know your file is different.
Adjust the three settings (spike threshold, near-duplicate distance, neighbors) if the defaults don’t suit your site.
Tap Validate points.
Read the results, starting with the red Critical section, then the orange Warnings.
Copy the clean data and import it into your software.
What your file should look like

Five fields per line, separated by commas: point number, northing, easting, elevation, description.

1000,45428.017,52275.954,61.27,EA-5(SM)
1001,45321.302,52352.931,62.11,EDGE-TAXIWAY

A header row is okay. The tool will spot it and remove it.

The left side: your inputs

Drop zone / browse. Accepts .txt, .csv, .prn and .xyz files.

Text area. Paste your points here, or edit what a file loaded. Fix a line, tap Validate again, and you’ll see the results update.

Column order.

Auto-detect from header: If line 1 is a header, it looks for the words “east” or “north” (or “lon”/”lat”) to work out the order. With no header, it assumes PNEZD.
PNEZD (Northing first): Use this when your file has northing before easting.
PENZD (Easting first): Use this when easting comes first. The tool flags it and swaps the columns in the export.

Elevation spike threshold (default 50). For each point, the tool finds its nearest neighbors with the same description, takes their median elevation, and compares. If your point is off by more than this number, it’s flagged. Use your data’s units. On flat terrain like a runway, try something small like 1 or 2. On hilly ground, keep it larger so you don’t get false alarms.

Near-duplicate distance (default 0.06). Flags two points that sit closer together than this distance but aren’t identical. This catches double shots and re-occupied points. Set it to 0 to switch the check off.

Neighbors compared (same code) (default 4, range 2 to 12). How many nearby same-code points are used to work out that median for the spike check. A higher number smooths things out. A lower number is more sensitive to local changes.

Validate points runs the check. Clear empties the text area and the results.

The right side: your results

Three summary boxes at the top: the count of critical flags, the count of warnings, and the number of points that made it into the clean export.

✕ Critical flags (red). These break imports, and the tool fixes them in the export:

Line 1 is a header (removed)
A line doesn’t have exactly 5 fields (removed)
Non-numeric coordinates or elevation, or a blank point number (removed)
Duplicate point numbers (later one removed)
Identical coordinates on two points (later one removed)
Columns in PENZD order (swapped)

! Warnings (orange). These need your judgment, and nothing gets removed:

Elevation spikes, listed worst first
Blank descriptions
Descriptions ending in a stray _ or /
Combined codes with a / that may not match a single code in your list
Inconsistent spellings of the same feature, like EA-5(SM) and EA-5
Near-duplicate points
Point numbers that drop out of order (harmless, just a heads-up)

Under the warnings you’ll also see the elevation range and the largest local deviation. That tells you how close your data came to the threshold.

✓ Clean export (green). The cleaned data in PNEZD order, comma-delimited, with a header row. Your descriptions stay exactly as you wrote them.

Copy clean data copies the whole thing to your clipboard.
Export to CSV only appears inside Claude’s hosted environment. In a regular browser, use Copy and paste into a text file.
Tips
Fix critical flags first. Warnings are worth a look, but they won’t stop an import.
The export includes a header row. If your software doesn’t expect one, delete the first line before importing.
Always compare the “points exported” number to your original count so you know exactly how many were dropped.
