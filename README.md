# soundwave
Tests for a smooth Bezier curve visualizer for Rainmeter

1.0>1906092154+8: Initial Release

Important: If any changes to the variables are made, you must run the Auto-Configuration Program to compile and apply them.

Soundwave is a test for producing a visualizer in the form of smoothly connected Bezier curves.

### Skins:
**Visualizer** (Soundwave\main.ini)
Key object that is used to display the audio spectrum. The context menu includes the ability to change the variables file (var.inc) and run the Auto-Configuration Program.

**Song Information** (Soundwave\songname\sec.ini)
Basic secondary object that displays the artist and song title.
Note: If only the song title is available, only it is displayed. If the song title is unavailable, nothing is displayed even if the artist name is given.

Auto-Configuration Program (Soundwave\autoconfig\program.ini)
Must be ran for a second after variables are changed.

### Variables:
(Only these may be changed, others that may be included do nothing)

**xconst** Width modifier. (default 25)
**yconst** Height modifier. (default 80)
**endsize** Start and end "flat line" length modifier. (default 80)
**player** Music player to retrieve song information from. (default Spotify)

### Other Visualizer Options:
The visualizer's refresh rate can be changed at the top of its file (default 50 ms (20 Hz))
The visualizer's gradient can be changed at the bottom of its file.
The number of frequency bands is hard-coded with dependencies and it may be difficult to change.

### How It Works
1. The values for each frequency band are found normally with AudioLevel.
2. Each value is translated into a y-value and "virtual points" the curve must pass are created.
3. The gradient of the tangent at each point is found by averaging the angle between a given point and the previous point, and the given point and the next point.
4. The control points of the individual Bezier curves are found using the gradient in (3).
5. The line is produced by joining the individual Bezier curves in a Shape meter.
