# Paddle Up

Courtside team-picking and running ratings for a pickleball group: who is here,
what the night should look like, and how everyone's form is moving.

**This repository holds no game data of its own.** Opened with nothing else
supplied, the app shows `sample.csv` -- a hundred games among eight players who
do not exist, so you can see it actually work. Point it at a real group with a
`csv` parameter on the address:

    https://<user>.github.io/<repo>/?csv=<address of a published CSV>

The CSV wants a header row and then one row per game, the same shape as
`sample.csv` in this repository:

    Date,Team 1 - Player 1,Team 1 - Player 2,Team 2 - Player 1,Team 2 - Player 2,Team 1 Score,Team 2 Score
    10/8/2025,Ann,Ben,Cal,Dee,5,11

In Google Sheets that address comes from **File -> Share -> Publish to web**,
choosing **Comma-separated values (.csv)**. Anything else that serves CSV over
https with cross-origin reads allowed will do.

**Copy a link with this source**, in the app's *Where the games come from*
section, turns whatever is loaded back into a shareable address.

Ratings are a ridge regression of score differential on a team matrix, refitted
over a sliding window; a player's value is the points per game they add to
their side. Everything runs in the page -- there is no backend, and nothing
leaves the device.
