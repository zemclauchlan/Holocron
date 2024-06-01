---
dg-publish: true
---

## High Score

  

To store high scores the data needs to be saved to the local drive - this is known as persistent data (the data persists even if the application is not running).

  

Before implementing any form of persistent data, the exact data that needs to be save must be determined. The points where the data is loaded from and saved to the local drive must be decided.

  

Your application must also be prepared for attempting to load the data, however it doesn’t exist at that time - such as when the application is run for the first time.

  

Godot has an inbuilt system to save data and nodes to the local drive, however this tutorial will focus on only saving and loading the previous high scores.

  

Before implementing persistent data, there are a few topics to understand - where the user data is stored and serialisation.

  

## Godot User Data

  

Most file access performed in Godot begins with `res://` (e.g. `res://Menu/Menu.tscn`), which refers to the project root folder (the folder containing `project.godot`). A file path starting with `res://` looks for the file relative to that root folder.

  

User data uses the `user://` prefix which points to a different folder which is not in the project folder.

  

> The `user://` prefix points to a different directory on the user's device. On mobile and consoles, this path is unique to the project. On desktop, the engine stores user files in:

`~/.local/share/godot/app_userdata/[project_name]` on Linux, 

`~/Library/Application Support/Godot/app_userdata/[project_name]` on macOS (since Catalina) and

 `%APPDATA%\Godot\app_userdata\[project_name]` on Windows.

[https://docs.godotengine.org/en/stable/tutorials/io/data_paths.html](https://docs.godotengine.org/en/stable/tutorials/io/data_paths.html)

>

  

## Serialisation

  

Serialisation is the process of preparing data and objects to save to disk or transmitted.

  

## Testing!

  

Testing the high score system and the saving and loading of data can be frustrating as the tester needs to try for different scores to ensure that the rank order is correct.

  

One method for improving this process is to add a cheat code into the game.

  

For instance, in the `Player.gd` script, the script can be updated to check if the user presses the Up key. If so, this changes the scene straight to the win scene.s

  

![Screen Shot 2022-04-30 at 11.34.35 pm.png](Notionimp/images/Screen_Shot_2022-04-30_at_11.34.35_pm.png)

  

- Code

```python

if Input.is_action_pressed("ui_up"):

get_tree().change_scene("res://WinScene.tscn")

```

  

## High Scores

  

Currently, the game may have a simple scoring system, with only the currentScore being used.

  

This will be expanded upon by implementing not only a highScore variable as shown, but also the top 3 scores, as well as the current players score.

  

<aside>

‼️ Note: the players name is not within the scope of the tutorial at this stage. If you wish to implement this, you will need to track the names as well, collecting the data within your game.

  

</aside>

  

```gdscript 

var scoringInformation = {

"currentScore": 0,

"currentPlayer": "User",

"highScore": 0,

"highScorePlayersName" : "Winner"

}

```

  

### Global.gd

  

Start by expanding `scoringInformation` to track the first, second and third top scores. This is done in Global.gd.

  

The starting values for each can be 0. As each player completes the game, their score will be compared to the top score, and if greater, then shift the values down.

  

This is implemented through an array. The first element is the highest score, and down from there.

  

```gdscript

var scoringInformation = {

"currentScore": 0,

"currentPlayer": "User",

"highScores": [0,0,0],

"highScorePlayersName" : "Winner"

}

```

  
### Win Scene

  

When the player wins the game, the Win Scene is loaded. It will be at this point that their score (stored in `scoringInformation`) will be compared to the high scores.

  

- If your win Scene doesn’t have a script attached

Add a script to the root node by right-clicking on it and choosing Attach Script. Choose the default settings.

![Screen Shot 2022-04-30 at 10.22.57 pm.png](Notionimp/images/Screen_Shot_2022-04-30_at_10.22.57_pm.png)

  

Remove the unnecessary code, leaving only the extends command on the first line, and `func _ready()` function.

  

![Screen Shot 2022-04-30 at 10.24.59 pm.png](Notionimp/images/Screen_Shot_2022-04-30_at_10.24.59_pm.png)

  

Update the _ready() function to store the current players score into the array in the correct position, if necessary.

  

![Screen Shot 2022-04-30 at 11.20.04 pm.png](Notionimp/images/Screen_Shot_2022-04-30_at_11.20.04_pm.png)

  

- Code

```python

func _ready():

# Sorts the array

GlobalVariables.scoringInformation["highScores"].sort()

# Searches the array for the value, or the position in the array where it will "fit".

var highScorePosition = GlobalVariables.scoringInformation["highScores"].bsearch(GlobalVariables.scoringInformation["currentScore"], true)

print("position #", highScorePosition)

# Inserts the value into the array at the correct position.

GlobalVariables.scoringInformation["highScores"].insert(highScorePosition, GlobalVariables.scoringInformation["currentScore"])

# Removes the first (and lowest) score.

GlobalVariables.scoringInformation["highScores"].remove(0)

# Debugging.

print(GlobalVariables.scoringInformation["highScores"])

```

  

The high score system has been implemented!

  

$* \normalsize \mathcal {\color{black} \colorbox {orange} {Save, Commit and Push Changes to Github!}}$

  

## Persistent Data

  

In this tutorial, you’ll be shown how to save and load the `scoringInformation` dictionary.

  

<aside>

❓ In this tutorial, only a small amount of data will be saved and loaded, so not a lot of focus on serialisation is done. However if the game requires saving more complex data, you will need to ensure this is done.

  

</aside>

  

Open [Global.g](http://Global.gs)d and create a new global variable which sets the save file.

  

![Screen Shot 2022-05-01 at 12.24.52 am.png](Notionimp/images/Screen_Shot_2022-05-01_at_12.24.52_am.png)

  

- Code

```python

var saveFile = "user://save.dat"

```

  

### Saving the data

  

To ensure it’s saved when it is updated, the saving of high score data can be done in the Win Scene.

  

Open `WinScene.gd` and create a new function called `saveData()`.

  

![Screen Shot 2022-05-01 at 12.20.42 am.png](Notionimp/images/Screen_Shot_2022-05-01_at_12.20.42_am.png)

  

- Code

```python

func saveData():

```

  

Update `saveData()` to attempt to access the file name specified in `Global.gd` called `saveFile`. If there is no issues with that file, it will write the scoringInformation dictionary to the file and close the connection.

  

![Screen Shot 2022-05-01 at 12.25.56 am.png](Notionimp/images/Screen_Shot_2022-05-01_at_12.25.56_am.png)

  

- Code

```python

func saveData():

var file = File.new()

var error = file.open(GlobalVariables.saveFile, file.WRITE)

if error == OK:

file.store_var(GlobalVariables.scoringInformation)

file.close()

print("!!Data Saved!!")

else :

print("!!Data Not Saved!!")

```

  

Lastly, update the `_ready()` function to call the `saveData()` function.

  

![Screen Shot 2022-05-01 at 12.33.02 am.png](Notionimp/images/Screen_Shot_2022-05-01_at_12.33.02_am.png)

  

### Loading the Data

  

Open the main menu and look at the script for the scene - `Menu.gd`.

  

Update the `_ready()` function to load (or attempt to load) the saved data.

  

This code checks to see if the file exists first - applications don’t like attempting to open files that don’t exist.

  

If the file is there, it replaces the `scoringInformation` data that’s coded by default with the loaded data. If there is any error, it just leaves the default values.

  

![Screen Shot 2022-05-01 at 12.34.49 am.png](Notionimp/images/Screen_Shot_2022-05-01_at_12.34.49_am.png)

  

- Code

```python

var file = File.new()

if file.file_exists(GlobalVariables.saveFile):

var error = file.open(GlobalVariables.saveFile, File.READ)

if error == OK:

var player_data = file.get_var()

file.close()

GlobalVariables.scoringInformation = player_data

```

  

$* \normalsize \mathcal {\color{black} \colorbox {orange} {Save, Commit and Push Changes to Github!}}$

  

## Bug or Feature?

  

There’s a bug with the saving and loading of `scoringInformation`. Did you notice? It’s got to do with currentScore - it’s not resetting correctly and is saving the current score in the save file.
