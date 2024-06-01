
## Win & Lose Conditions

  

The Win and Lose conditions refer to the state of gameplay to determine whether the player “wins” the game or “loses” the game. Those states are determined by the game itself and what occurs after is up to the developer.

  

Some examples could be:

  

- Win Condition

- All enemies are killed

- The door at the end of the level is opened

- The player survives the night

- etc.

- Lose Condition

- The player’s health reaches 0.

- The player runs out of ammunition.

- etc.

  

In our clone of space invaders, the following conditions exist (at a minimum)

  

| Win Condition/s | Lose Condition/s |

| --- | --- |

| All enemies are defeated | The timer reaches 0. |

| | The player’s health reaches 0. |

  

## Win Condition

  

Expand each of the following to implement the different conditions.

  

### All Enemies are Defeated

  

Open `MainGame.tscn`, and click on the “Open in Editor” button next to one of the individual enemy nodes.

  

![Screen Shot 2022-04-30 at 10.30.47 pm.png](Notionimp/images/Screen_Shot_2022-04-30_at_10.30.47_pm.png)

  

This opens the original scene to edit. All of the individual enemies in the game are based on this one scene.

  

With the root node selected, click on the Node tab, then click on Groups. Enter “enemy” and click Add.

  

![Screen Shot 2022-04-30 at 10.31.40 pm.png](Notionimp/images/Screen_Shot_2022-04-30_at_10.31.40_pm.png)

  

Save the scene. This adds this tag to each individual enemy.

  

Return to Main Game.

  

Open `MainGame.gd`, and in the `_process()` function, check if there are no more nodes with the tag enemy left. If there are none, then go to the Win Scene.

  

```python

func _process(delta):

$HUD/CurrentScore.text = str(GlobalVariables.scoringInformation["currentScore"])

if get_tree().get_nodes_in_group("enemy").size() == 0:

get_tree().change_scene("res://WinScene.tscn")

```

  

Change `res://WinScene.tscn` to link to the Win Scene in your project.

  

## Lose Condition

  

Expand each of the following to implement the different conditions.

  

### The Timer Reaches 0

  

To implement this condition check, open the MainGame.gd script and look in the _ready() function.

  

![Screen Shot 2022-04-26 at 11.18.58 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.18.58_pm.png)

  

If Line 17 is reached, it outputs `Game Over` to the console, which means the timer has reached 0. This is where the code will need to go to make it perform a function. Luckily the condition check has already been performed!

  

Create a New Scene through the `Scene` Menu

  

![Screen Shot 2022-04-26 at 11.21.23 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.21.23_pm.png)

  

Choose Node2D in the hierarchy tab to start the scene, and then Right Click on the Node2D and choose `Add Child Node`.

  

![Screen Shot 2022-04-26 at 11.21.40 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.21.40_pm.png)

  

Search for, and add, a VBoxContainer

  

![Screen Shot 2022-04-26 at 11.21.57 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.21.57_pm.png)

  

Rename the VboxContainer as Layout. Right click on that, and choose Add Child Node.

  

![Screen Shot 2022-04-26 at 11.22.15 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.22.15_pm.png)

  

This time, search for and add a Label

  

![Screen Shot 2022-04-26 at 11.22.25 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.22.25_pm.png)

  

Rename the Label as Heading, and then change the text attribute to “You Lost” or anything else appropriate.

  

![Screen Shot 2022-04-26 at 11.22.52 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.22.52_pm.png)

  

Now add a button as a child of the VboxContainer called Layout.

  

![Screen Shot 2022-04-26 at 11.23.21 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.23.21_pm.png)

  

Change the text to `Return to the Main Menu,` or anything else appropriate.

  

![Screen Shot 2022-04-26 at 11.23.42 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.23.42_pm.png)

  

Right click on the button in the heirarchy and choose `Attach Script`.

  

![Screen Shot 2022-04-26 at 11.24.26 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.24.26_pm.png)

  

Don’t change any of the defaults and just click Create.

  

![Screen Shot 2022-04-26 at 11.24.32 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.24.32_pm.png)

  

With the button selected, switch to the Node tab as shown.

  

![Screen Shot 2022-04-26 at 11.23.57 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.23.57_pm.png)

  

Double click on the `pressed` signal.

  

![Screen Shot 2022-04-26 at 11.24.14 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.24.14_pm.png)

  

Don’t change anything here - just click `Connect`.

  

![Screen Shot 2022-04-26 at 11.24.49 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.24.49_pm.png)

  

Change the script to the code shown below.

  

```python

func _on_Button_pressed():

get_tree().change_scene("res://Menu/Menu.tscn")

```

  

<aside>

❓ Note that the `res://Menu/Menu.tscn` may need to be modified to match your project. It needs to be the path to *your* main menu scene.

  

</aside>

  

![Screen Shot 2022-04-26 at 11.25.18 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.25.18_pm.png)

  

![Screen Shot 2022-04-26 at 11.25.27 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.25.27_pm.png)

  

Save the Scene.

  

![Screen Shot 2022-04-26 at 11.25.45 pm.png](Notionimp/images/Screen_Shot_2022-04-26_at_11.25.45_pm.png)

  

Go back to MainMenu.gd and after the print("Game Over") code, you will need to add the following:

  

```python

get_tree().change_scene("res://LoseScene.tscn")

```

  

<aside>

❓ Remember the scene linked will need to match *your* project. Change `res://LoseScene.tscn` to whatever you need to link it to the scene you just created.

  

</aside>

  

### The Player’s Health Reaches 0.

  