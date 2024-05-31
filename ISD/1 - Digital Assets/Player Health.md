---
dg-publish: true
---

To enable health in the player, a few scripts need to be updated. Open `Player.gd` and add a new function at the bottom of the script to reduce the health of the player.

  

<aside>

‼️ Depending on your requirements, you can change the value that health is reduced by.

  

</aside>

  

![Untitled](Work/ISD/1%20-%20Digital%20Assets/images/Untitled%206.png)

  

```python

func reduceHealth():

health -= 1

if health == 0:

get_tree().change_scene("res://Menu/Menu.tscn")

```

  

At the top of the script, add a new variable called `health` which can also be configured in the Godot IDE by including the `export` keyword.

  

![Untitled](Work/ISD/1%20-%20Digital%20Assets/images/Untitled%207.png)

  

```python

export (int) var health = 1

```

  

Save the script.

  

Open `Bullet-Enemy.gd` and update the code which runs when the bullet collides with an option. This code will check if the collidedObject contains the word “Player”, and if so, run the `reduceHealth()` function on that object.

  

Save the script.

  

![Untitled](Work/ISD/1%20-%20Digital%20Assets/images/Untitled%208.png)

  

```python

if "Player" in collidedObject.collider.name:

collidedObject.collider.reduceHealth()

```

  

Test the functionality.

  

Commit the changes.

  