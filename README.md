
## Behaviour Tree

My BT is set up around 2 main flows:

1. **Patrol flow** (default):
   - Pick / move to patrol locations.
   - Keep looping while the player is not detected.

2. **Reaction flow** (after perception trigger):
   - Switch from patrol to reaction/chase behavior when the player is sensed.
   - If the player is lost, leave reaction mode and return to patrol.
     
3. - Shoot player when in range.
   

## Blackboard keys used

- `TargetActor` - stores the detected player actor (or `None` when not detected).
- `EnemyClose` - (bool) - true when player is within range.
- `CanSeePlayer` (bool) - true when the perception sense is currently detecting the player.

## AIPerception setup (exactly one sense)

I used **Sight** as the only active AIPerception sense.

It creates two clearly different states:

- **Before detection:** AI is patrolling.
- **After detection:** AI visibly reacts (switches into chase/alert behavior).

When sight is lost (player hides/leaves view), the AI clears detection state and goes back to patrol.

This repository includes Git LFS tracking

- Patrol before detection
- The sight trigger causing a visible state change
- Attack/shoot when player is in radius
- Return to patrol after detection is lost


