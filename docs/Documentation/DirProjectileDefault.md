<style>
.spacer {
	padding-top: 10px;
	padding-bottom: 25px;
}
</style>
<style>
.nowrap {
	overflow: hidden;
    white-space: nowrap;
}
</style>

#DirProjectileDefault

In: res://projectile/DirProjectileDefault.gd

Inherits: StateInterface > [ObjectState](https://rmld00dlenoodles.github.io/YOMIDoku/Documentation/ObjectState) > DirProjectileDefault.gd

(Note that this doesn't have a class name; extend from the file path instead.)

##Description

Default projectile state for directional projectiles.

##Properties

|Property|Default Value|Description|
|:-----:|:-----:|:-----:|
|`move_speed` | "15.0" | How quickly the projectile should move. Used for non-homing projectiles.|
|`homing` | false | Whether the projectile actively tracks opponents.|
|<p class="nowrap">`homing_turn_speed`</p> | "3.0" | How quickly the projectile turns while tracking an opponent.|
|`homing_accel` | "1.0" | How quickly the projectile accelerates when tracking an opponent.|
|<p class="nowrap">`max_homing_speed`</p> | "10" | The projectile's maximum speed when tracking an opponent|
|`start_homing` | false | Whether or not the projectile should be aimed based on `data["dir"]` when starting this state.|
|`lifetime` | 999999 | If the projectile has been in this state for longer than this number of ticks, it fizzles.|

##Enumerations

<p>There are no enumerated types for this class.</p>

##Constants

|Constant|Value|Description|
|:-----:|:-----:|:-----:|
|`FREE_AFTER_TICKS` | 60 | Unknown use, presumably for garbage collection.|

##Methods

<div class="spacer"></div>

`_frame_1()`

Runs on the first tick of the state. Initializes `hit_something` and `hit_something_tick`, and sets the host's `is_grounded` to false. if `homing` is true, also sets initial velocity based on whether or not `start_homing` is also true. 

returns `null`

<div class="spacer"></div>

`_tick()`

Runs each tick.
If the projectile collides with a wall or the ground, run `fizzle()`.
If the projectile has lived longer than its `lifetime`, run `fizzle()`.
If the projectile has not hit anything, check if the projectile is supposed to be homing or not. If not, move the projectile directly based on `data["dir"]`; if it is, calculate and apply a force to push it towards `host.creator.opponent` based on the parameters provided.

returns `null`

<div class="spacer"></div>

`_got_parried()`

Called when a hitbox belonging to this state is parried. If `homing` is true, immediately calls `fizzle()`

returns `null`.

<div class="spacer"></div>

`fizzle()`

Disables the host and terminates all hitboxes. Also sets `hit_something` to true and `hit_something_tick` to the current tick.

returns `null`

<div class="spacer"></div>

`_on_hit_something(obj, _hitbox)`
Runs upon colliding with an object. Immediately calls `fizzle()`.

returns `null`

<div class="spacer"></div>

##Signals

<p>There are no signals for this class.</p>

##Credits

Info contributed by [xColdxFusionx](https://rmld00dlenoodles.github.io/YOMIDoku/about/#attributions)

##Source

??? abstract "DirProjectileDefault.gd"
	```gd
	extends ObjectState

	const FREE_AFTER_TICKS = 60

	export  var _c_Projectile_Dir = 0
	export  var move_speed = "15.0"

	export  var _c_Homing_Options = 0
	export  var homing = false
	export  var homing_turn_speed = "3.0"
	export  var homing_accel = "1.0"
	export  var max_homing_speed = "10"
	export  var start_homing = false
	export  var lifetime = 99999
	export  var relative_data_dir = false

	var hit_something = false
	var hit_something_tick = 0

	func _frame_1():
		
		hit_something = false
		hit_something_tick = 0
		host.set_grounded(false)
		if homing:
			if start_homing:
				var dir = data["dir"]
				var move_vec = fixed.normalized_vec_times(str(dir.x), str(dir.y), move_speed)
				host.apply_force(move_vec.x, move_vec.y)
			else :
				host.apply_force_relative(move_speed, "0.01")

	func _tick():
		var pos = host.get_pos()
		host.update_grounded()
		if current_tick > 1 and not hit_something and host.is_grounded() or pos.x < - host.stage_width or pos.x > host.stage_width:
			fizzle()
			host.hurtbox.width = 0
			host.hurtbox.height = 0
			pass
		if current_tick > lifetime:
			fizzle()
			host.hurtbox.width = 0
			host.hurtbox.height = 0
		elif not hit_something:
			var dir
			if not homing:
				dir = data["dir"]
				var dir_x = fixed.mul(dir.x, str(host.get_facing_int())) if relative_data_dir else dir.x
				var move_vec = fixed.normalized_vec_times(dir_x, str(dir.y), move_speed)
		
				host.move_directly(move_vec.x, move_vec.y)
				host.sprite.rotation = float(fixed.vec_to_angle(dir.x, dir.y))
			else :
				var target = host.obj_local_center(host.creator.opponent)
				var vel = host.get_vel()
				var current = fixed.normalized_vec(vel.x, vel.y)
				var desired = fixed.normalized_vec(str(target.x), str(target.y))
				var steering_x = fixed.sub(desired.x, current.x)
				var steering_y = fixed.sub(desired.y, current.y)
				var steer_force = fixed.normalized_vec_times(steering_x, steering_y, homing_turn_speed)
				var force_x = fixed.mul(current.x, homing_accel)
				var force_y = fixed.mul(current.y, homing_accel)
				if not fixed.eq(vel.x, "0"):
					host.set_facing(1 if fixed.gt(vel.x, "0") else - 1)
				host.apply_force(force_x, force_y)
				host.apply_force(steer_force.x, steer_force.y)
				host.apply_forces()
				
				host.update_data()
				var new_vel = host.get_vel()
				if fixed.gt(fixed.vec_len(new_vel.x, new_vel.y), max_homing_speed):
					var clamped_vel = fixed.normalized_vec_times(new_vel.x, new_vel.y, max_homing_speed)
					host.set_vel(clamped_vel.x, clamped_vel.y)
				host.sprite.rotation = float(fixed.vec_to_angle(fixed.mul(new_vel.x, str(host.get_facing_int())), new_vel.y))

	func _got_parried():
		if homing:
			fizzle()

	func fizzle():
		hit_something = true
		host.disable()
		terminate_hitboxes()
		hit_something_tick = current_tick

	func _on_hit_something(_obj, _hitbox):
		fizzle()
	```