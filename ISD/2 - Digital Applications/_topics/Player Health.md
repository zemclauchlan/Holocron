This stage of the tutorial will demonstrate how to implement a simple health system, where there is a player health and when the enemy collides with the player, the health reduces. As with many other aspects of game development, the exact implementation will depend on the requirements for the project, so apply as necessary.

> [!note] This process can be applied to ANY object that you wish to reduce the players health when a collision occurs.

# Player Script

## Create Health Variable

Open `Player.gd` and add a new variable named `player_health`. Set the initial value to be 100.

Save the file.

![[playerHealthVariable.png]]

## Detect Collision

Update the `_physics_process()` function to detect any collections that occur *after* the `move_and_slide()` function call.

![[playerHealthCollisionDetection.png]]

```gdscript
for i in get_slide_collision_count():
		var collision = get_slide_collision(i)
		print("I collided with ", collision.get_collider().name)
```

Run this code, and the debug output will include many lines of text to indicate all the objects that the Player is colliding with.

![[playerHealthCollisionOutput.png]]

This output is simply indicating the name of the node in the hierarchy that the Player is colliding with.

![[playerHealthEnemyName.png]]

### Detect Enemy
There are different ways to proceed from here. The two options covered here are:
- Using the objects name
- Using the objects group


#### Option 1 - Using the name

he code could check the name of the object detected to see if the word "Enemy" is in the name and then act on it. This would work for enemies named "Enemy1", "Enemy2", "BossEnemy" etc. however is limited in that it will only work with objects with Enemy in the name. So, it wouldn't work for a force field called "Forcefield" even if you want the same action to occur.

The code for this option would be:

![[playerHealthDetectEnemyName.png]]

```gdscript
if "Enemy" in collision.get_collider().name:
	player_health -= 10
```


#### Option 2 - Using the group

> [!note] This option is more flexible than the first.
> This approach focuses on the objects *group* rather than the name. This allows you to have any object reduce health from the player instead of ones with "Enemy" in the name.

![[playerHealthDetectEnemyGroup.png]]

```gdscript
if collision.get_collider().is_in_group("enemy"):
	player_health -= 10
```

# Reduce Health function

To standardise the process for removing health from the player, create a new function to handle the steps. Call the function similar to this: `reduce_health(10)`

![[playerHealthReduceHealthFunction.png]]

```gdscript
func reduce_health(amount):
	player_health -= amount
```

## Players death

In the new function, add a check to see if the players health reaches 0, and if so, end the game.

![[playerHealthDeath.png]]

```gdscript
if player_health < 0:
	# The player dies. 
	# Go back to the main menu. This can be changed to any scene in the future.
	get_tree().change_scene_to_file("res://Menus/main_menu.tscn")
```

# Update Enemy

Open `Enemy.tscn` to edit the Enemy scene, adding an `Area` node as a child of the root node. Add a CollisionShape node a child of that one.

![Screen Shot 2022-09-12 at 8.56.53 pm.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b3dc548e-f7df-4d10-94d4-1bde0fdaf283/Screen_Shot_2022-09-12_at_8.56.53_pm.png)

Select `CollisionShape` and change the shape attribute to a `CapsuleShape`.

![Screen Shot 2022-09-12 at 8.58.22 pm.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3d87ab97-b394-4933-b508-10f79a7dc2f2/Screen_Shot_2022-09-12_at_8.58.22_pm.png)

Select Area in the hierarchy, change to the Node tab, and double click on `body_entered()` in the list of signals.

![Screen Shot 2022-09-12 at 8.59.56 pm.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7cdcbc56-99c1-4b7a-9956-ce390aea80d7/Screen_Shot_2022-09-12_at_8.59.56_pm.png)

Click Connect.

![Screen Shot 2022-09-12 at 9.02.37 pm.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/581cf8ab-09d8-4bf9-9803-74be31ef1d34/Screen_Shot_2022-09-12_at_9.02.37_pm.png)

Replace the contents of the function with the code shown.

This code checks first if the object the enemy has collided with is the player, and if so, reduce `player_health` by 10. Then delete the enemy object from the game.

<aside> ‼️ The exact value the health gets reduced by can be set to whatever value you chose. Just change the 10.

</aside>

![Screen Shot 2022-09-12 at 9.06.39 pm.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/83f6a6dc-3765-4008-9223-3d8abaa4cc9a/Screen_Shot_2022-09-12_at_9.06.39_pm.png)

```python
if (body.name == "Player"):
		Global.player_health -= 10
		queue_free()
```

Save the Enemy script.

# Lose Scene

If not already done, create a new scene and save it as `Lose.tscn`. This scene will be loaded if the player has lost, or in this example, run out of health.

Design the scene in whichever way you wish, just ensure there is a way for the user to return to the main menu.

# Update Player Script

Open the Player script (`Player.gd`) and add the code to the end of the `_process()` function.

![Screen Shot 2022-09-12 at 9.42.29 pm.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/335f08cd-d47e-4268-a0f3-b7bbf9e60029/Screen_Shot_2022-09-12_at_9.42.29_pm.png)

```python
if Global.player_health <= 0:
		print("Dead")
		get_tree().change_scene("res://Lose.tscn")
```

![[commonBlocks#Commit & Push]]