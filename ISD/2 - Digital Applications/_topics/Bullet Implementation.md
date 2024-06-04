There are numerous ways to implement shooting in an FPS (or other type of) game. 

The first is through creating projectiles (such as bullets) for the player to shoot. The bullets will hit objects in their direct path, and can cause damage. This method is the focus for this section of the project.

Another method, is to use <tooltip term="raycast">raycasts</tooltip>, where the there is an imaginary line drawn from the camera, and seeing what object it hits first (if any). Raycasts will be covered in a later tutorial.

> What are the pros and cons of each approach? Why choose one over the other?


## Bullet Mesh

> This tutorial is going to demonstrate how to create a simple bullet. Your implementation for the model may differ, however the process should be the same.
{style="note"}

Create a new Scene (Scene→New Scene).

Set the Root Node as `Area3D` by selecting Other Node and search for Area3D.

![Untitled](bullet-RootNode.png)

Create your bullet model. You can create your own mesh, or you can follow the instructions shown below.

### Simple Bullet

For a simple bullet shape, this can be done by creating a `CSGCylinder3D` and a `CSGSphere3D` and manipulating (move and rotate) them into a bullet shape.

![Screen Shot 2022-10-04 at 9.47.38 pm.png](bullet-PositionNodes.png)

Ensure that both of these CSG objects have Union Operation selected.

![Screen Shot 2022-10-04 at 9.45.55 pm.png](bullet-UnionOperation.png)

Then place them as children of a `CSGCombiner3D`. Name the new node as appropriate.

![Untitled](bullet-Combiner.png)

Texture the object as you would normally.

> Search for "Metallic texture seamless" to find a metal texture for a bullet.
{style="note"}

![Screen Shot 2022-10-04 at 9.51.14 pm.png](bullet-Textured.png)

Attach a `CollisionShape3D` node as a child of the scene root.

![Untitled](bullet-CollisionShape3D.png)

With the `CollisionShape3D` selected, set the Shape to be `CapsuleShape3D`.

![Screen Shot 2022-10-04 at 9.55.49 pm.png](bullet-SetCollisionShape.png)

Manipulate the Capsule shape, using the transform options, so that it completely surrounds the mesh.

![Untitled](bullet-ManipulateCapsule.png)

Rename the Scene Root as `Bullet`.

![Screen Shot 2022-10-04 at 9.59.07 pm.png](bullet-RenameRoot.png)

Save the scene as `Bullet.tscn`.

![Untitled](bullet-SaveScene.png)

![[commonBlocks#Commit & Push]]

## Bullet Script

Still in the Bullet scene, attach a new script to the root node (Bullet) and name it `Bullet.gd`.

![Untitled](bullet-AttachScript1.png)

![Untitled](bullet-AttachScript2.png)

Add two new variables to control how fast the bullet will travel, and how much damage it will inflict on the object it collides with (if configured to take damage). 

> These can be set to whatever values are appropriate.
{style="info"}

| Variable | Type    | Description                                                             |
|----------|---------|-------------------------------------------------------------------------|
| `speed`  | `float` | How fast the bullet will move through the game.                         |
| `damage` | `int`   | How much damage the bullet will inflict on the object it collides with. |


> This can be used to allow for different weapons with different bullet speeds and damage.
{style="info"}

<tabs>
<tab title="Screenshot">
<img src="bullet-Variables.png" alt="Variables"/>
</tab>
<tab title="Code">
<code-block>
var speed : float = 30.0
var damage : int = 1
</code-block>
</tab>
</tabs>


Add code, within the `_process` function to move the bullet instance forward. 

<tabs>
<tab title="Screenshot">
<img src="bullet-ScriptMoveBullet.png" alt="Moving the bullet" />
</tab>
<tab title="Code">
<code-block>
func _process (delta):
    # move the bullet forwards
    global_transform.origin -= transform.basis.z.normalized() * speed * delta
</code-block>
</tab>
</tabs>

Save the Script.

Select the root node (Bullet) and change to the Node tab. 

![Untitled](bullet-ChangeToNode.png)

Double click on `body_entered`. Press **Connect.**

This code will be used to detect when the bullet instance has collided with another object - when the bullet collider enters another node’s collider.

![Untitled](bullet-Signal.png)

In order to only destroy objects that need to be destroyed, this code will first check if the other collider has a function called `take_damage` in its script. This means that a script attached to the enemy objects can have that function, and will take damage, however a wall doesn't need that function, so it won’t be destroyed.

 `_on_Bullet_body_entered(body)` executes when the bullet enters another object. If that object has the `take_damage()` function (or method), it will then run that function on the other node, passing the `damage` value.

Also added is the `destroy()` function. This simply deletes the bullet from the game.

This has been added in such a way to allow for future modification as required.

<tabs>
<tab title="Screenshot">
<img src="bullet-ScriptDamageDestroy.png" alt="Bullet Damage and Destroy" />
</tab>
<tab title="Code">
<code-block>
func _on_Bullet_body_entered(body):
    if body.has_method("take_damage"):
        body.take_damage(damage)
        destroy()
func destroy():
    queue_free()
</code-block>
</tab>
</tabs>


## Automatically deleting the bullet

A potential problem with creating instances of bullets is that the player could create 1000s of bullets that would continue running in the game, flying off into the distance, taking up valuable processing power. A solution for this problem is to automatically delete the bullets after a set time.

In the bullet scene, create a **Timer** child node of the root note

![Screen Shot 2022-10-04 at 10.22.24 pm.png](bullet-CreateTimerNode.png)

Set the wait time to something appropriate, and Autostart to On.

![Untitled](bullet-TimerSettings.png)

Change to the Node tab and double-click on the `timeout()` signal. 

Set the Receiver Method to `destroy`.

> You can either type in the function name, or use the Pick button to choose the correct function.
{style="note"}

Select Connect.

![Untitled](bullet-TimerSignal.png)

![Untitled](bullet-TimerSignalConnect.png)

Save the Bullet Scene.

![[commonBlocks#Commit & Push]]