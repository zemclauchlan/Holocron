Every FPS needs an enemy!

> [!info]- Which `Body` is best?
> In this tutorial, you'll be creating a RigidBody3D for the enemy. The player node was created as a CharacterBody3D. Why the change?
> The basic physic bodies work like this:
> - `StaticBody3D`: It does not move.
> - `CharacterBody3D`: You move it.
> - `RigidBody3D`: The physics engine moves it.

# Create a Scene

Create a new scene (`File`→ `New Scene`) and create the root node as a `RigidBody3D`. This will be the root node of the enemy object.

![[enemyNewRoot.png]]
![[enemyCharacterBody3d.png]]

Rename the node as `Enemy`.

![[enemyRename.png]]

Add a `MeshInstance3D` as a child of `Enemy`.

![[enemyAddMeshInstance3D.png]]

Click on the down arrow next to Mesh and choose New CapsuleMesh.

> [!note] This can be created as whatever type of object you wish, or a custom Mesh.

![[enemyNewCapsule.png]]

Ensure that the capsule is *vertical*. This simulates the character's body, so needs to stand upright. If the capsule is not vertical, change the rotate values to make it look like this.

![[enemyVerticalCapsule.png]]

# Timer

Add a Timer node as a child of enemy.
![[enemyNewTimer.png]]

With the Timer selected, set the wait time to something appropriate and set it to Autostart.

In this case, the enemy will wait 2 seconds before starting to move towards the player.

![[enemyTimerSettings.png]]


# Collision Shape

The last step is to create a Collision Shape (hitbox) for it to interact with other objects in the game.

Create a `CollisionShape3D` child node of Enemy.

![[enemyCollisionShape3D.png]]

With the CollisionShape3D selected, set the Shape attribute to a Capsule.

> [!note] If you set the MeshInstance3D to be any other shape than a capsule, you may need to modify this step to match.

![[enemyCollsionShape.png]]

# Save The Scene

Save the scene as `enemy.tscn`. 

![[enemySaveScene.png]]


![[commonBlocks#Commit & Push]]