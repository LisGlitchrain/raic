# Local runners

You have an option to run simple test games locally on your computer. To do so, download the Local runner utility. Use of that utility will allow you to test your strategy in an environment similar to the environment of a testing game on the site, but without any restrictions on the number of games created.

By default, runner waits for your strategy client to connect on port 31001. This is also the default port used by any language pack. To connect your strategy to the runner, first start the runner, and then start your strategy (run compiled program or run Runner.<ext> file in scripted languages)

Last version: January 11, 2019 - v1.1.1

**Possible arguments for runner** (you can also see this in ./codeball2018 --help)**:**

*    ```--team-size <size>``` — team size (default is ```2```).
*    ```--p1 <player1>``` — First player (default is ```tcp-31001```). Possible values are ```tcp-<port>```, ```keyboard```, ```helper```, ```empty```
*    ```--p2 <player2>``` — Second player (default is ```helper```). Possible values are ```tcp-<port>```, ```keyboard```, ```helper```, ```empty```
*    ```--p1-name <player_name>``` / ```--p2-name <player_name>``` — Player names for showing in scores table
*    ```--nitro <true/false>``` — Turn nitro on/off (default is ```false```)
*    ```--duration <ticks>``` — Game duration in ticks, by default is 5 * 60 * 60 = 18000.
*    ```--log-file <path>``` — Path to file to save game log
*    ```--replay <path>``` — Path to game log file to replay
*    ```--noshow``` — Turn off visualization
*    ```--start-paused``` — Start paused
*    ```--no-countdown``` — Turn off countdown in the beginning of the game and after each goal
*    ```--until-first-goal``` — Finish game when first goal is scored
*    ```--fast-forward <tick>``` — Start viewing from specified tick
*    ```--seed <int>``` — Specify game seed
*    ```--vsync``` — Turn vertical synchronization on
*    ```--export-arena <path>``` — Export arena model to the specified file in obj format

Also, **runner allows you to show some debug information on the screen** (shown when you select schematic rendering). To do so, override ```custom_rendering``` / ```customRendering``` method of ```MyStrategy```. The method is called once per tick after calling ```act``` method for all of your robots.

This method should return string that will be shown on the screen. Debug information is saved in runner for each tick, so it works with rewinding.

Also, if the returned string can be correctly parsed into a special JSON, you can also show spheres/lines/text. JSON is a list of objects to show. For example (here r,g,b,a — red/green/blue/alpha components of color):

```json
[
  {
    "Sphere": {
      "x": 2.0,
      "y": 5.0,
      "z": 15.0,
      "radius": 0.1,
      "r": 1.0,
      "g": 0.0,
      "b": 0.0,
      "a": 0.5
    }
  },
  {
    "Text": "Debug text #0"
  },
  {
    "Line": {
      "x1": 0.0,
      "y1": 0.0,
      "z1": 0.0,
      "x2": 10.0,
      "y2": 20.0,
      "z2": 30.0,
       "width": 1.0,
       "r": 1.0,
       "g": 1.0,
       "b": 1.0,
       "a": 1.0
    }
  }
]
```
