# The Core - Animations

## Project Overview
This project is built upon the base animations and functionality covered in class and extends them with additional features to enhance character movement and interaction. The focus has been on improving functionality rather than retargeting Mixamo animations, aiming for reusable mechanics for the upcoming Intermediate Project 2.

---

## Base Features (Covered in Class)
- Idle and walk blendspace (unarmed)
- Idle and walk blendspace (armed)
- Jump and fall cycle
- Weapon aim offset
- Weapon attach to right hand
- Left arm IK for weapon holding
- Equip animation
- Weapon attach to back
- Weapon shooting
- Simple melee combo

---

## Additional Features
### Crouch
**CharacterBP & Inputs:**
- Utilized Unreal's built-in `Crouch` and `UnCrouch` functions to handle capsule size changes and collision management efficiently.
- CameraBoom adjusts distance when crouching/uncrouching for a smoother visual effect.

**Animations:**
- Unarmed: Added a blendspace (BS) for idle/walk/run, following the same structure as unarmed movement.
- Armed: Implemented a 2D BS, cached poses, and integrated them into the `WeaponMotion` state machine.
- Ensures seamless crouch-to-jump and crouch-to-combo transitions.

### Lean
- Created two variations of unarmed forward walk animations, tilted 10° left and right.
- Implemented a BS using movement yaw for blending, providing a natural leaning effect while walking or running.
- Not applied to armed movement due to fixed forward-facing rotation.

### Foot IK
- Integrated Foot IK from Unreal’s Third-Person ABP, adapting it to our custom ABP.
- Fixed deprecated function issues preventing correct bone transformations.

### Vault
**CharacterBP & Logic:**
- Implemented `Vault` functionality using raycasts to detect vaultable surfaces.
- Used Motion Warping with an Animation Montage for smooth transitions.
- Ensures correct landing position with additional validation checks.
- Disabled gravity and collisions during vaulting to prevent unintended physics interactions.

**Animations:**
- `AM_VaultOver`: Animation montage with motion warp notifies.
- `MDT_VaultRifle`: Used a Mirror Data Table to adjust right-hand support animation for cases when the weapon is equipped.
- Created a separate branch to disable left-hand IK when vaulting with a weapon.

### Climb
**CharacterBP & Logic:**
- Developed a climbing system with logic for detecting climbable surfaces, edge transitions, and motion warping.
- Functions include:
  - `CanClimb`: Uses raycasts to determine climbable surfaces.
  - `ClimbMovement`: Handles movement, ledge detection, and input processing.
  - `StopClimbing`: Restores normal movement state after climbing.
  - `IsOnAnEdge`: Detects lateral wall edges and triggers a fall.
  - `IsAtLedgeOrMantle`: Determines if the player is at a climbable ledge.
  - `Ledge/MantleExecution`: Executes ledge transitions using motion warping.
  - `CalculateLedgeWarpPoints`: Defines precise motion warp targets for smooth transitions.

**Animations:**
- `BS_Climb`: Simple blendspace for vertical and horizontal climbing movements.
- `AM_MantleLedge`: Animation montage for ledge climbing, with motion warp notifies.
- Used a dedicated FullBody animation slot to prevent blending issues.

### Character Model
- Used a character model from Fab due to time constraints.
- Some models had different skeletons, requiring socket adjustments.
- Chose the current model for compatibility and ease of use.

---

## Areas for Improvement
1. **Weapon Blend Space:**
   - Some movement directions (backward, diagonal forward-left) have inconsistencies.
   - Adding animations for 8 directions could improve blending.

2. **Climbing Ledge Transition:**
   - The final ledge grab movement is not fully refined, especially from certain distances.
   - A motion warp adjustment step before the final transition could enhance accuracy.

---

## Conclusion
This project integrates various advanced animation and movement mechanics, focusing on a smooth and responsive character experience. Future improvements will refine motion transitions and expand the climbing system for better precision and realism.

For any feedback or contributions, feel free to submit issues or pull requests in the repository!

