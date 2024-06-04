
> **Prerequisites** - A bullet (or any projectile) scene needs to have been created and saved according to the instructions given on this site. If you have created your own method, you will have to adapt this as necessary.

With the bullet created, the game now needs to be configured to *shoot* the bullet. Initially, this will be done in the player script.

First, the code will need to know **where** to create the bullet instances. 

Open `Player.tscn` and create a `Node3D` node as a child of the Camera. Name it `bulletSpawn`.  

![Untitled](bulletShooting-bulletSpawn.png)

In 3d mode, move `bulletSpawn` to be in front of the camera. 

> It might take some experimentation to make it look correct during game play. You may need to change the position a number of times.
{style= "tip"}

![Untitled](bulletShooting-bulletSpawnPosition.png)

Open `Player.gd` and add the code to preload the bullet and configure the spawn point.

> Important - the path to the bullet scene and the bulletSpawn point need to be **exactly** as you’ve defined them in your project. If they are named as something else, your code needs to reflect that.
{style="warning"}

<tabs>
<tab title="Screenshot">
<img src="bulletShooting-PreloadBullet.png" alt="Preload Bullet"/>
</tab>
<tab title="Code">
<code-block>
var bulletScene = preload("res://Scenes - Other/bullet.tscn")
var bulletSpawn
</code-block>

<code-block>
bulletSpawn = get_node("Camera3D/bulletSpawn")
</code-block>
</tab>
</tabs>


Add a new variable to keep track of the ammunition the player is carrying.

Set the value to something appropriate for your project.

<tabs>
<tab title="Screenshot">
<img src="bulletShooting-Ammo.png" alt="Bullet Ammo"/>
</tab>
<tab title="Code">

<code-block>
var ammo : int = 15
</code-block>
</tab>
</tabs>


Create a new function - `shoot()`- which will run when the shoot input is detected.

> Change `/Root/Doom` to the name of your root node in the game scene. E.g. `/Root/MainGame`
{style="note"}

![Untitled](bulletShooting-RootGame.png)

<tabs>
<tab title="Screenshot">
<img src="bulletShooting-ScriptShoot.png" alt="Bullet Ammo"/>
</tab>
<tab title="Code">
<code-block>
func shoot ():
    var bullet = bulletScene.instantiate()
    get_node("/root/Doom").add_child(bullet)
    bullet.global_transform = bulletSpawn.global_transform
    bullet.scale = Vector3(0.1,0.1,0.1)
    ammo -= 1
</code-block>
</tab>
</tabs>

Update `_physics_process()` to check to see if the player has pressed the `shoot` input. 

<tabs>
<tab title="Screenshot">
<img src="bulletShooting-PlayerInput.png" alt="Player Input check"/>
</tab>
<tab title="Code">
<code-block>
if Input.is_action_just_pressed("player_shoot"):
    shoot()
</code-block>
</tab>
</tabs>


Run the game at this stage to test the creation and shooting of bullet instances.


![[commonBlocks#Commit & Push]]