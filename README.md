# Roll a Ball

This is my first foray into Unity development, where I built a basic rolling ball game. I've always loved playing games and have heard of Unity on numerous occasions as the leading game development platform. Hence, I was really excited to have the chance to play around with the tool and learn more about game objects, models, components, prefabs, scripting, and building. I used Unity's standard assets for this exercise, but am thrilled to explore their asset store for more visuals on my next project.

##Key Things I Learned

### How collisions work in Unity's physics engine
* Physics engine does not allow 2 collider items to overlap
* When physics engine detects that any 2 or more items will overlap with that frame, the physics engine will eanalyze their speed, rotation, and shape, and then calculate collision.

### Collisions mainly determined by Static or Dynamic Objects/Geometry
* Static Object/Collider: non-moving parts of your scene (walls, floor courtyard, ground)
* Dynamic Object/Collider: moving parts (player, car).
    * Physics engine can allow overlop or penetration of collider volumes. When it does this, the physics engine still calculates the collider volumes and collider overlap but doesn't physcially act on the overlapping objects.
    * Doesn't cause collision by itself. Need to actually implement Unity triggers

### Triggers / Trigger Colliders
  * Can detect contact iwth collider via on trigger event messages
  * ex: trigger on door. when step into elevator
  * use onTriggerEnter()

### Caching
  * Static objects are naturally cached, but if you implement special rules like rotating feature on one, the physics engine rules would account for these values. Adding it to the cache uses extra resources in the app and is inefficient.
  * To cache, add rigid body to dynamic components only like rotating cubes
  * Dynamic object: has collider and a rigid body component.
    * Add rigid bodies since apply physics forces.
    * Apply kinematic and gravity rules
    * Kinematic: a kinematic rigid body will not react to physics forces and can be animated and moved by it's transform. moved using it's transform
  * ex: triggers like collectibles that need to be moved by it's transform, entering elevator. Makes a dynamic object performant
  * Static object: if has collider and no rigid body component

### How Text is Added
  * Added as UI components
  * Must be within a canvas to operate properly
  * Can create a public variable on your player and make sure to record the change on Start and onTriggerEnter. Then drag the UI text to the Player's PlayerController script
