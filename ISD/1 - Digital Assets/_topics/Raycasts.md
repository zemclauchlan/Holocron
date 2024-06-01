---
dg-publish: true
---

```
Raycasts are an invisible line between two points in game. Using Raycasts you can detect collisions (or potential collisions). They have a number of uses such as calculating the destination of a bullet, without creating (instantiating) a bullet in game, or if an object can ‘see’ another object (if there’s a wall in the way).
```
  

In the project, open the `enemy.tscn` file to edit the enemy object. This will update **all** enemy instances in the game.

  

Add a child node to the Enemy. Search for RayCast2D in the list and choose Create.

  

![Screen Shot 2022-05-31 at 9.18.52 pm.png](Notionimp/images/Screen_Shot_2022-05-31_at_9.18.52_pm.png)

  

With the new RayCast2D node selected, change the Inspector values `Enabled` and `Cast To:.`

  

![Screen Shot 2022-05-31 at 9.28.31 pm.png](Notionimp/images/Screen_Shot_2022-05-31_at_9.28.31_pm.png)

  

Attach a script to the RayCast2D node.

  

![Screen Shot 2022-05-31 at 9.23.38 pm.png](Notionimp/images/Screen_Shot_2022-05-31_at_9.23.38_pm.png)

  

![Screen Shot 2022-05-31 at 9.23.43 pm.png](Notionimp/images/Screen_Shot_2022-05-31_at_9.23.43_pm.png)

  

Replace the contents with the following code.

  

Save the script.

  

```arduino

extends RayCast2D

  

# Called when the node enters the scene tree for the first time.

func _ready():

set_process(true)

  

func _process(delta):

if self.is_colliding():

get_parent().canShoot = false

else:

get_parent().canShoot = true

```

  

Open Enemy.gd and create a new variable, declaring it at the top of the script.

  

```arduino

var canShoot = false

```

  

![Screen Shot 2022-05-31 at 9.24.41 pm.png](Notionimp/images/Screen_Shot_2022-05-31_at_9.24.41_pm.png)

  

**Update** the _process() function to first check if canShoot is true. If it is true, then the normal ‘shooting’ code will execute.

  

<aside>

‼️ You only need to add the following line to the function - `if canShoot:`.

  

</aside>

  

![Screen Shot 2022-05-31 at 9.26.59 pm.png](Notionimp/images/Screen_Shot_2022-05-31_at_9.26.59_pm.png)
