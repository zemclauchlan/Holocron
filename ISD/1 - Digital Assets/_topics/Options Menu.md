
## Options Implementation

  

## Scene Creation

  

With the Space Invaders project open, Create a new scene.

![[optionsNewScene.png]]  


  

When the choice appears, choose User Interface out of the four options.

  

<aside>

✔️ It is possible to also create it as a 2D Scene.

  

</aside>

  
![[optionsRootNode.png]]


  

Rename the scene `OptionsMenu`.

  
![[optionsRootNodeRename.png]]


  

Add a VBoxContainer node as a child of `OptionsMenu`. Rename the node as `Layout`

  
![[optionsNodeLayout.png]]


  

Create a CheckButton node as a child of Layout. Rename this to `RapidFireSelect`.

  ![[optionsAddButton.png]]



  

Set the text property of this box to Rapid Fire.

  

![Screen Shot 2022-04-29 at 1.41.12 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.41.12_pm.png)

  

As another child of `Layout`, create a Button, renamed to `ReturnToMainMenu`.

  

![Screen Shot 2022-04-29 at 1.06.59 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.06.59_pm.png)

  

Set the text property of `ReturnToMainMenu` button to “Return to the Main Menu”

  

![Screen Shot 2022-04-29 at 1.34.08 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.34.08_pm.png)

  

Save the Scene as OptionsMenu, saving it in a folder called Options in the root of the project.

  

![Screen Shot 2022-04-29 at 1.00.48 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.00.48_pm.png)

  

At the end of this process, your Scene and FileSystem should appear similar to this.

  

![Screen Shot 2022-04-29 at 1.02.06 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.02.06_pm.png)

  

### Button Functionality

  

To quickly add the functionality to the single `ReturnToMainMenu` button in the scene, you can add a function to run with the button is pressed.

  

Right-click on the `ReturnToMainMenu` button and choose Attach Script.

  

![Screen Shot 2022-04-29 at 1.16.55 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.16.55_pm.png)

  

Leave the settings and just click Create.

  

![Screen Shot 2022-04-29 at 1.17.05 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.17.05_pm.png)

  

Leave the script for the moment, and select the `ReturnToMainMenu` button in the hierarchy. Change to the Node options and double click on the Pressed() signal.

  

![Screen Shot 2022-04-29 at 1.11.17 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.11.17_pm.png)

  

The Connect a Signal to a Method dialog appears. Leave all the values as is, and click Connect. This will take you back to the script with a new function created.

  

![Screen Shot 2022-04-29 at 1.20.55 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.20.55_pm.png)

  

Change the pass command to the code shown, Godot will assist you by showing a menu with all the scenes. Choose your Main Menu scene from the list.

  

`get_tree().change_scene(`

  

![2022-04-29 13-22-37.2022-04-29 13_23_16.gif](Notionimp/images/2022-04-29_13-22-37.2022-04-29_13_23_16.gif)

  

### Link from the Main Menu

  

Open the main menu scene.

  

![Screen Shot 2022-04-29 at 1.29.44 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.29.44_pm.png)

  

Right Click on the `OptionsMenu.tscn` and choose Copy Path.

  

![Screen Shot 2022-04-29 at 1.28.38 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.28.38_pm.png)

  

Select the Options Button in the hierarchy and set the Scene To Load variable in the Inspector to the path to the options menu.

  

![Screen Shot 2022-04-29 at 1.31.07 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.31.07_pm.png)

  

### Test the Buttons

  

Run the project, and check to make sure you can navigate from the Main Menu to the Options menu and back again.

  

![2022-04-29 13-35-40.2022-04-29 13_36_03.gif](Notionimp/images/2022-04-29_13-35-40.2022-04-29_13_36_03.gif)

  

## Rapid Fire Implementation

  

### Global Variable

  

Open Global.gd and create a new variable called rapidFire and set it to `false`.

  

```python

var rapidFire = false

```

  

Save the script.

  

![Screen Shot 2022-04-29 at 1.48.24 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.48.24_pm.png)

  

### Options Menu functionality

  

Now that the scene has been created, successfully linked and the global variable set, it’s now time to implement the Rapid Fire option.

  

<aside>

✔️ Remember: This can be done for any option that will be used throughout the game. For instance, this could be used to set the difficulty setting, audio volume etc.

  

</aside>

  

Open the OptionsMenu Scene.

  

Right click on RapidFireSelect and choose Attach Script.

  

![Screen Shot 2022-04-29 at 1.41.57 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.41.57_pm.png)

  

Leave the settings on the dialog box and choose Create.

  

You do not need to make any changes to the code at this stage.

  

![Screen Shot 2022-04-29 at 1.42.11 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.42.11_pm.png)

  

With the button selected, change to the Node view and double click on the toggled signal.

  

![Screen Shot 2022-04-29 at 1.52.02 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.52.02_pm.png)

  

Leave all the settings as default and click on the Connect button.

  

![Screen Shot 2022-04-29 at 1.52.08 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.52.08_pm.png)

  

The default code is created.

  

![Screen Shot 2022-04-29 at 1.53.34 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.53.34_pm.png)

  

Replace the pass code with code to set the `rapidFire` variable in the Global script.

  

<aside>

‼️ This code works because the value that the check button is set to (on or off) equates to `true` or `false` which can set the rapidFire value in the global script.

  

</aside>

  

![Screen Shot 2022-04-29 at 1.54.52 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.54.52_pm.png)

  

```python

GlobalVariables.rapidFire = button_pressed

```

  

### Using the Options

  

This has now completed this section as the collection and storage of the options through the menu. The next stage is to use this within the rest of the game.

  

In this case, the `rapidFire` variable can be used in the Player.gd script to modify the functionality for the firing process.

  

- Code

```python

func _process(delta):

if GlobalVariables.rapidFire:

if Input.is_action_pressed("fire"):

var bulletInstance = bulletSource.instance()

bulletInstance.position = Vector2(position.x, position.y-20)

get_tree().get_root().add_child(bulletInstance)

else:

if Input.is_action_just_pressed("fire"):

var bulletInstance = bulletSource.instance()

bulletInstance.position = Vector2(position.x, position.y-20)

get_tree().get_root().add_child(bulletInstance)

```

  

![Screen Shot 2022-04-29 at 1.58.58 pm.png](Notionimp/images/Screen_Shot_2022-04-29_at_1.58.58_pm.png)

  