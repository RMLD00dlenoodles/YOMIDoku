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

#ObjectState

In: res://ObjectState.gd

Inherits: StateInterface > [ObjectState](https://rmld00dlenoodles.github.io/YOMIDoku/Documentation/ObjectState)

##Description

Base code for states. This applies to both player and projectile states.

##Properties

|Property|Default Value|Description|
|:-----:|:-----:|:-----:|
|`apply_forces` | false | Whether or not the state should calculate movement based on forces.|
|`apply_fric` | false | Whether or not the state should account for friction when determining movement.|
|`apply_grav` | false | Whether or not the state should account for gravity when determining movement.|
||||
|`fallback_state` | "Wait" | The state to move to automatically when this state ends.|
|`sprite_animation` | "" | The animation to play for this state.|
|`anim_length` | 1 | How many ticks this state lasts.|
|`sprite_anim_length` | -1 | How many frames of the animation to use. (-1 defaults to the full animation)|
|`ticks_per_frame` | 1 | How many ticks each frame of the animation should last.|
|`loop_animation` | false | Whether or not the animation should loop, or freeze on the last frame.|
|`endless` | false | If true, the object will not enter the fallback state once the animation ends.|
||||
|`force_dir_x` | "0.0" | The x component of the timed force's direction.|
|`force_dir_y` | "0.0" | The y component of the timed force's direction.|
|`force_speed` | "0.0" | The magnitude of the timed force.|
|`force_tick` | 0 | The tick on which the timed force is performed.|
||||
|`enter_force_dir_x` | "0.0" | The x component of the entry force's direction.|
|`enter_force_dir_y` | "0.0" | The y component of the entry force's direction.|
|`enter_force_speed` | "0.0" | The magnitude of the entryforce.|
|`reset_momentum` | false | Whether or not the object's momentum is reset upon entering this state.|
||||
|`particle_scene` | null | A scene (ParticleEffect) to be spawned when entering the state.|
|`particle_position` | Vector2() | The position at which to spawn `particle_scene`.|
|<p class="nowrap">`spawn_particle_on_enter`</p> | false | Whether or not the game should attempt to spawn `particle_scene` when entering the state.|
||||
|<p class="nowrap">`timed_particle_scene`</p> | null | A scene (intended to be ParticleEffect) to be spawned when entering the state.|
|<p class="nowrap">`timed_particle_position`</p> | Vector2() | The position at which to spawn `timed_particle_scene`.|
|<p class="nowrap">`timed_spawn_particle_tick`</p> | 1 | The tick on which to spawn `timed_particle_scene`, if applicable.|
||||
|`enter_sfx` | null | AudioStream to play when entering the state.|
|`enter_sfx_volume` | -15.0 | Volume modifier for `enter_sfx`.|
|`sfx` | null | AudioStream to play during the state.|
|`sfx_tick` | 1 | What tick to play `sfx` during.|
|`sfx_volume` | -15.0 | Volume modifier for `sfx`.|
||||
|`projectile_scene` | N/A | A scene (intended to be BaseProjectile) to be spawned during the state.|
|`projectile_tick` | 1 | The tick on which to spawn `projectile_scene`.|
|`projectile_pos_x` | 0 | The horizontal offset of the projectile.|
|`projectile_pos_y` | 0 | The vertical offset of the projectile.|
|<p class="nowrap">`projectile_local_pos`</p> | true | Whether or not the projectile's spawn location is an absolute or relative position.|
||||
|`throw_positions` | {} | Dictionary containing position vectors. Can be set using the CharStateEditor; used for complex throw animations.|
||||
|`enter_sfx_player` | N/A | VariableSound2D for playing `enter_sfx`.|
|`sfx_player` | N/A | VariableSound2D for playing `sfx`.|
||||
|`current_tick` | -1 | Current tick of the state, as used for animation purposes.|
|`current_real_tick` | -1 | Current tick of the state, ignoring animation looping.|
|`fixed` | N/A | FixedMath for fixed-point calculations.|
||||
|`anim_name` | N/A | Name of the current animation.|
||||
|`has_hitboxes` | false | Whether or not the state has hitboxes.|
|`current_hurtbox` | null | The user's current hurtbox.|
|<p class="nowrap">`hitbox_start_frames`</p> | {} | Lists when the user's hitboxes activate, and which ones.|
|<p class="nowrap">`hurtbox_state_change_frames`</p> | {} | Lists when the user's hurtbox changes, and to which ones.|
|`frame_methods` | [] | List of frames with scripting tied to them.|
|`max_tick` | -1 | Tracks the highest tick the state has reached.|

##Enumerations

<p>There are no enumerated types for this class.</p>

##Constants

<p>There are no constants for this class.</p>

##Methods

<div class="spacer"></div>

`apply_enter_force()`

Applies a force based on the `enter_force` parameters.

returns `null`

<div class="spacer"></div>

`_on_hit_something(obj, _hitbox)`

Called when a hitbox in this state collides with something.

returns `null`

<div class="spacer"></div>

`get_projectile_pos()`

Returns a Dictionary containing the projectile's starting position.

returns `Dict`

<div class="spacer"></div>

`get_projectile_data()`

Returns `null` by default.

returns `null`

<div class="spacer"></div>

`process_projectile(_projectile)`

Does nothing by default.

returns `null`

<div class="spacer"></div>

`get_active_hitboxes()`

Returns all active hitboxes in the state.

returns `array`

<div class="spacer"></div>

`_tick_before()`

Processing performed at the beginnnig of each tick. Does nothing by default.

returns `null`

<div class="spacer"></div>

`process_feint()`

Returns the fallback state by default.

returns `string`

<div class="spacer"></div>

`_tick_shared()`

Shared per_tick processing for all states. Updates things such as hitboxes, hurtboxes, `current_tick` counters, and movement.
Returns a string if the processing detects that the state needs to be updated; otherwise, returns nothing.

returns `string, null`

<div class="spacer"></div>

`process_hitboxes()`

Activates and deactivates hitboxes based on the current tick.

returns `null`

<div class="spacer"></div>

`update_hurtbox()`

Updates the hurtbox based on any HurtboxState nodes available.

returns `null`

<div class="spacer"></div>

`_tick_after()`

Processing performed at the end of each tick. Updates hitbox positions based on the object's location.

returns `null`

<div class="spacer"></div>

`copy_data()`

Creates a copy of the state's data and returns it.

returns `data`

<div class="spacer"></div>

`copy_to(state:ObjectState)`

Copies the current state's properties to `state`'s properties.

returns `null`

<div class="spacer"></div>

`activate_hitbox(hitbox)`

Calls `hitbox.activate()`.

returns `null`

<div class="spacer"></div>

`terminate_hitboxes()`

Deactivates all hitboxes in the current state.

returns `null`

<div class="spacer"></div>

`deactivate_hitbox(hitbox)`

Does nothing by default.

returns `null`

<div class="spacer"></div>

`init()`

Performs initial setup for the state.

returns `null`

<div class="spacer"></div>

`setup_audio()`

Sets up required parameters for playing sound effects.

returns `null`

<div class="spacer"></div>

`setup_hitboxes()`

Sets up parameters for hitboxes.

returns `null`

<div class="spacer"></div>

`setup_hurtboxes()`

Sets up parameters for hurtboxes.

returns `null`

<div class="spacer"></div>

`__on_hit_something(obj, _hitbox)`

Called when detecting the signal `"hit_something"` from an attached hitbox. Calls `_on_hit_something()`.

returns `null`

<div class="spacer"></div>

`__on_got_parried()`

Called when detecting the signal `"got_parried"` from an attached hitbox. Calls `_got_parried()`.

returns `null`

<div class="spacer"></div>

`_got_parried()`

Does nothing by default.

returns `null`

<div class="spacer"></div>

`spawn_particle_relative(scene:PackedScene, pos = Vector2(), dir = Vector2.RIGHT)`

Spawns a particle effect at the listed position and direction relative to the user.

returns `null`

<div class="spacer"></div>

`_enter_shared()`

Shared processing upon entering the state.

returns `null`

<div class="spacer"></div>

`_exit_shared()`

Shared processing upon exiting the state. Resets the current hurtbox.

returns `null`

<div class="spacer"></div>

`xy_to_dir(x, y, mul="1.0", div = "100.0")`

Passthrough function for converting an X and Y value to a movement vector, with optional modifiers for speed.
Returns a Dictionary containing the results.

returns `Dict`

<div class="spacer"></div>

`update_sprite_frame()`

Updates the currently displayed sprite frame to match the current tick.

returns `null`

<div class="spacer"></div>

##Signals

`state_started()`

Emitted upon entering the state.

`state_ended()`

Emitted upon exiting the state.

##Credits

Info contributed by [xColdxFusionx](https://rmld00dlenoodles.github.io/YOMIDoku/about/#attributions)

##Source

??? abstract "ObjectState.gd"
	```gd
	extends StateInterface

	class_name ObjectState

	signal state_started()
	signal state_ended()

	export  var _c_Physics = 0
	export  var apply_forces = false
	export  var apply_fric = false
	export  var apply_grav = false

	export  var _c_Animation_and_Length = 0
	export  var fallback_state = "Wait"
	export  var sprite_animation = ""
	export  var anim_length = 1
	export  var sprite_anim_length = - 1
	export  var ticks_per_frame = 1
	export  var loop_animation = false
	export  var endless = false

	export  var _c_Static_Force = 0
	export  var force_dir_x = "0.0"
	export  var force_dir_y = "0.0"
	export  var force_speed = "0.0"
	export  var force_tick = 0

	export  var _c_Enter_Static_Force = 0
	export  var enter_force_dir_x = "0.0"
	export  var enter_force_dir_y = "0.0"
	export  var enter_force_speed = "0.0"
	export  var reset_momentum = false

	export  var _c_Particles = 0
	export (PackedScene) var particle_scene = null
	export  var particle_position = Vector2()
	export  var spawn_particle_on_enter = false

	export  var _c_TimedParticles = 0
	export (PackedScene) var timed_particle_scene = null
	export  var timed_particle_position = Vector2()
	export  var timed_spawn_particle_tick = 1

	export  var _c_Sfx = 0
	export (AudioStream) var enter_sfx = null
	export  var enter_sfx_volume = - 15.0
	export (AudioStream) var sfx = null
	export  var sfx_tick = 1
	export  var sfx_volume = - 15.0

	export  var _c_Projectiles = 0
	export (PackedScene) var projectile_scene
	export  var projectile_tick = 1
	export  var projectile_pos_x = 0
	export  var projectile_pos_y = 0
	export  var projectile_local_pos = true

	export  var _c_Auto = 0
	export  var throw_positions:Dictionary = {}

	var enter_sfx_player
	var sfx_player

	var current_tick = - 1
	var current_real_tick = - 1
	var fixed

	var anim_name

	var has_hitboxes = false

	var current_hurtbox = null

	var hitbox_start_frames = {
	}

	var hurtbox_state_change_frames = {
		
	}

	var frame_methods = []
	var max_tick = - 1

	func apply_enter_force():
		if enter_force_speed != "0.0":
			var force = xy_to_dir(enter_force_dir_x, enter_force_dir_y, enter_force_speed, "1.0")

			host.apply_force_relative(force.x, force.y)

	func _on_hit_something(_obj, _hitbox):
		pass

	func get_projectile_pos():
		return {"x":projectile_pos_x, "y":projectile_pos_y}

	func get_projectile_data():
		return null

	func process_projectile(_projectile):
		pass

	func get_active_hitboxes():
		var hitboxes = []
		for start_frame in hitbox_start_frames:
			var items = hitbox_start_frames[start_frame]
			for item in items:
				if item is Hitbox:
					hitboxes.append(item)
		return hitboxes

	func _tick_before():
		pass

	func process_feint():
		return fallback_state

	func _tick_shared():




		if current_tick == - 1:
			if spawn_particle_on_enter and particle_scene:
				var pos = particle_position
				pos.x *= host.get_facing_int()
				spawn_particle_relative(particle_scene, pos, Vector2.RIGHT * host.get_facing_int())
			apply_enter_force()

		current_real_tick += 1
		if current_tick < anim_length or endless:
			current_tick += 1

			process_hitboxes()

			update_sprite_frame()
			update_hurtbox()
			if current_tick == sfx_tick and sfx_player and not ReplayManager.resimulating:
				sfx_player.play()
			if current_tick == force_tick:
				if force_speed != "0.0":
					var force = xy_to_dir(force_dir_x, force_dir_y, force_speed, "1.0")
			
					host.apply_force_relative(force.x, force.y)

			if current_tick == projectile_tick:
				if projectile_scene:
					var pos = get_projectile_pos()
					var obj = host.spawn_object(projectile_scene, pos.x, pos.y, true, get_projectile_data(), projectile_local_pos)
					process_projectile(obj)

			if current_tick == timed_spawn_particle_tick:
				if timed_particle_scene:
					var pos = timed_particle_position
					pos.x *= host.get_facing_int()
					spawn_particle_relative(timed_particle_scene, pos, Vector2.RIGHT * host.get_facing_int())

			var new_max = false
			if current_tick > max_tick:
				max_tick = current_tick
				new_max = true
			
			if host.is_ghost or new_max or current_tick in frame_methods:
				var method_name = "_frame_" + str(current_tick)
				
				if has_method(method_name):
					if not (current_tick in frame_methods):
						frame_methods.append(current_tick)
					var next_state = call(method_name)
					if next_state != null:
						return next_state
				new_max = false

		if apply_fric:
			host.apply_fric()
		if apply_grav:
			host.apply_grav()
		if apply_forces:
			host.apply_forces()

	func process_hitboxes():
		if hitbox_start_frames.has(current_tick + 1):
			for hitbox in hitbox_start_frames[current_tick + 1]:
				activate_hitbox(hitbox)
		for hitbox in get_active_hitboxes():
			hitbox.facing = host.get_facing()
			if hitbox.active:
				hitbox.tick()
			else :
				deactivate_hitbox(hitbox)


	func update_hurtbox():
		if current_hurtbox:
			current_hurtbox.tick(host)
		if current_tick in hurtbox_state_change_frames:
			if current_hurtbox:
				current_hurtbox.end(host)
			current_hurtbox = hurtbox_state_change_frames[current_tick]
			current_hurtbox.start(host)

	func _tick_after():
		for hitbox in get_active_hitboxes():
			var pos = host.get_pos()
			hitbox.update_position(pos.x, pos.y)

	func copy_data():
		var d = null
		if data:
			if data is Dictionary or data is Array:
				d = data.duplicate()
			else :
				d = data
		return d

	func copy_to(state:ObjectState):
		var properties = get_script().get_script_property_list()
		for variable in properties:
			var value = get(variable.name)
			if not (value is Object or value is Array or value is Dictionary):
				if value:
					state.set(variable.name, value)
		state.data = copy_data()
		state.current_real_tick = current_real_tick
		state.current_tick = current_real_tick

	func activate_hitbox(hitbox):
		hitbox.activate()

	func terminate_hitboxes():
		for hitbox in get_active_hitboxes():
			hitbox.deactivate()

	func deactivate_hitbox(hitbox):

		pass

	func init():
		connect("state_started", host, "on_state_started", [self])
		connect("state_ended", host, "on_state_ended", [self])
		fixed = host.fixed
		anim_name = sprite_animation if sprite_animation else state_name
		if sprite_anim_length < 0:
			if host.sprite.frames.has_animation(anim_name):
				sprite_anim_length = host.sprite.frames.get_frame_count(anim_name)
			else :
				sprite_anim_length = anim_length
		setup_hitboxes()
		setup_hurtboxes()
		call_deferred("setup_audio")

	func setup_audio():
		if enter_sfx:
			enter_sfx_player = VariableSound2D.new()
			add_child(enter_sfx_player)
			enter_sfx_player.bus = "Fx"
			enter_sfx_player.stream = enter_sfx
			enter_sfx_player.volume_db = enter_sfx_volume

		if sfx:
			sfx_player = VariableSound2D.new()
			add_child(sfx_player)
			sfx_player.bus = "Fx"
			sfx_player.stream = sfx
			sfx_player.volume_db = sfx_volume

	func setup_hitboxes():
		var hitboxes = []
		for child in get_children():
			if child is Hitbox:
				hitboxes.append(child)
				host.hitboxes.append(child)
		for hitbox in hitboxes:
			hitbox.init()
			has_hitboxes = true
			hitbox.host = host
			if hitbox.start_tick >= 0:
				if hitbox_start_frames.has(hitbox.start_tick):
					hitbox_start_frames[hitbox.start_tick].append(hitbox)
				else :
					hitbox_start_frames[hitbox.start_tick] = [hitbox]
			hitbox.connect("hit_something", self, "__on_hit_something")
			hitbox.connect("got_parried", self, "__on_got_parried")
			for hitbox2 in hitboxes:
				if hitbox2.group == hitbox.group:
					hitbox.grouped_hitboxes.append(hitbox2)

	func setup_hurtboxes():
		for child in get_children():
			if child is HurtboxState:
				hurtbox_state_change_frames[child.start_tick] = child


	func __on_hit_something(obj, hitbox):
		if active:
			_on_hit_something(obj, hitbox)

	func __on_got_parried():
		if active:
			_got_parried()

	func _got_parried():
		pass

	func spawn_particle_relative(scene:PackedScene, pos = Vector2(), dir = Vector2.RIGHT):
		var p = host.get_pos_visual()
		host.spawn_particle_effect(scene, p + pos, dir)

	func _enter_shared():
		if reset_momentum:
			host.reset_momentum()
		current_tick = - 1
		current_real_tick = - 1
		if enter_sfx_player and not ReplayManager.resimulating:
			enter_sfx_player.play()
		emit_signal("state_started")

	func _exit_shared():
		if current_hurtbox:
			current_hurtbox.end(host)
		host.reset_hurtbox()

	func xy_to_dir(x, y, mul = "1.0", div = "100.0"):
		return host.xy_to_dir(x, y, mul, div)

	func update_sprite_frame():
		if ReplayManager.resimulating:
			return 
		if not host.sprite.frames.has_animation(anim_name):
			return 
		if host.sprite.animation != anim_name:
			host.sprite.animation = anim_name
			host.sprite.frame = 0
		var sprite_tick = current_tick / ticks_per_frame

		var frame = (sprite_tick % sprite_anim_length) if loop_animation else Utils.int_min(sprite_tick, sprite_anim_length)
		host.sprite.frame = frame
	```