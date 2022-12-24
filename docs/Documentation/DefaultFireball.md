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

#DefaultFireball

In: res://characters/stickman/projectiles/fireball_states/Default.gd

Inherits: StateInterface > [ObjectState](https://rmld00dlenoodles.github.io/YOMIDoku/Documentation/ObjectState) > DefaultFireball

##Description

Default state for projectiles. Contains most of the projectile's processing code.

##Properties
|Property|Default Value|Description|
|:-----:|:-----:|:-----:|
|<p class="nowrap">`move_x`</p> | 4 | Base horizontal speed of the projectile.|
|`move_y` | 0 | Base vertical speed of the projectile.|
|`clash` | true | Whether or not the projectile reacts to collisions with other entities.|
|`num_hits` | 1 | The number of hits the projectile can perform before disappearing.|
|`lifetime` | 999999 | If the projectile has been alive for this many frames and has not been disabled, it will be disabled automatically.|
|<p class="nowrap">`fizzle_on_ground`</p> | true | Whether or not the projectile fizzles upon hitting the ground.|
|<p class="nowrap">`fizzle_on_walls`</p> | true | Whether or not the projectile fizzles upon hitting a wall.|

##Enumerations

There are no enumerated types for this class.

##Constants

A list of constants, alongside a brief description and their values in the following format:

|Constant|Value|Description|
|:-----:|:-----:|:-----:|
|`FREE_AFTER_TICKS` | 60 | Unknown use, presumably for garbage collection.|

##Methods

<div class="spacer"></div>

`_frame_0()`

Runs on the tick before the state begins. Initializes `hit_something` and `hit_something_tick`, and sets the host's `is_grounded` to false.

returns `null`

<div class="spacer"></div>

`_tick()`

Runs each tick.
If the projectile collides with a wall or the ground, run `fizzle()`.
If the projectile has lived longer than its `lifetime`, run `fizzle()`.
If the projectile has not hit anything, move the projectile, adding `data["speed_modifier"]` if applicable.

returns `null`

<div class="spacer"></div>

`_on_hit_something(obj, _hitbox)`

Runs upon colliding with an object.
If `clash` is true, check if `obj` is a BaseProjectile. If it is and `deletes other projectiles` is false, do nothing.
If `clash` is true and either of the additional checks fail, reduce `num_hits` by 1. If this reduces the value to 0, run `fizzle()`.

returns `null`

<div class="spacer"></div>

`fizzle()`

Disables the host and terminates all hitboxes. Also sets `hit_something` to true and `hit_something_tick` to the current tick.

returns `null`

<div class="spacer"></div>

##Signals

<p>There are no signals for this class.</p>

##Credits

Info contributed by [xColdxFusionx](https://rmld00dlenoodles.github.io/YOMIDoku/about/#attributions)


##Source

??? abstract "Default.gd"
	```gd
	extends ObjectState

	class_name DefaultFireball

	const FREE_AFTER_TICKS = 60

	export  var _c_Projectile_Dir = 0
	export  var move_x = 4
	export  var move_y = 0
	export  var clash = true
	export  var num_hits = 1
	export  var lifetime = 999999
	export  var fizzle_on_ground = true
	export  var fizzle_on_walls = true

	var hit_something = false
	var hit_something_tick = 0

	func _frame_0():
		hit_something = false
		hit_something_tick = 0
		host.set_grounded(false)

	func _tick():
		var pos = host.get_pos()
		host.update_grounded()
		if not hit_something and ((host.is_grounded() and fizzle_on_ground) or (fizzle_on_walls and (pos.x < - host.stage_width or pos.x > host.stage_width))):
			fizzle()
			host.hurtbox.width = 0
			host.hurtbox.height = 0
			pass
		if current_tick >= lifetime:
			fizzle()
		elif not hit_something:
			if data and data.has("speed_modifier"):
				host.move_directly_relative((move_x + data["speed_modifier"]) if move_x != 0 else 0, (move_y + data["speed_modifier"]) if move_y != 0 else 0)
			else :
				host.move_directly_relative(move_x, move_y)

	func _on_hit_something(obj, _hitbox):
		if clash:
			if obj is BaseProjectile:
				if not obj.deletes_other_projectiles:
					return 
			num_hits -= 1
			if num_hits == 0:
				fizzle()

	func fizzle():
		hit_something = true
		host.disable()
		terminate_hitboxes()
		hit_something_tick = current_tick
	```