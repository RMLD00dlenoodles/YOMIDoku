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

#BaseChar.md

In: res://characters/BaseChar.gd

Inherits: BaseObj

##Description

Defines the Fighter class from which every YOMI Hustle character inherits.
Contains properties that determine character metadata and variables that are useful as accessors.

##Properties

|Property|Default Value|Description|
|:-----:|:-----:|:-----:|
|`MAX_HEALTH`|1000|The health of your fighter.|
|<p class="nowrap">`num_air_movements`</p>|2|The amount of air options your fighter has.|
||||
|<p class="nowrap">`character_portrait`</p>|N/A|The portrait that will show in character select.|
|`you_label`|$you_label|The label that shows over your character when you control them.|
|`actionable_label`|1000|The label that shows over your prediction ghost on the frame you will be active.|
|`quitter_label`|$"%QuitterLabel"|The label that shows over your character after you leave, briefly before you blow up. Shame on you.|
||||
|`input_state`|InputState.new()|N/A|
|`color`|Color.white|N/A|
||||
|<p class="nowrap">`player_info_scene`</p>|N/A|The playerinfo scene your character uses.|
|<p class="nowrap">`player_extra_params_scene`</p>|N/A|N/A|
||||
|<p class="nowrap">`damage_taken_modifier`</p>|"1.0"|Multiplier for this fighter's damage taken.|
|`num_feints`|2|Presumably the number of free cancels the player can make from neutral.|
||||
|`opponent`|N/A|Reference to the parent node of the enemy fighter; commonly used as an accessor from character states.|
||||
|`queued_action`|null|N/A|
|`queued_data`|null|N/A|
|`queued_extra`|null|N/A|
||||
|<p class="nowrap">`dummy_interruptable`</p>|false|N/A|
||||
|`game_over`|false|Likely set to true when MAX_HEALTH hits 0.|
|`forfeit`|false|N/A|
|`will_forfeit`|false|N/A|
||||
|`applied_style`|null|N/A|
|`is_color_active`|false|N/A|
|`is_aura_active`|false|N/A|
|`is_style_active`|null|N/A|
||||
|`ivy_effect`|false|?????|
||||
|<p class="nowrap">`colliding_with_opponent`</p>|true|Presumably a check for collisionbox overlaps between fighters.|
||||
|<p class="nowrap">`air_movements_left`</p>|0|The amount of air options your fighter currently has.|
||||
|`action_cancels`|{}|N/A|
||||
|`ghost_ready_tick`|null|N/A|
|`ghost_ready_set`|false|N/A|
|`got_parried`|false|True if your move was successfully parried by the opponent.|
||||
|`di_enabled`|true|Value determined from pre-match settings; enables DI if true.|
|`turbo_mode`|true|Value determined from pre-match settings; enables Turbo Mode if true.|
|<p class="nowrap">`infinite_resources`</p>|true|Value determined from pre-match settings; enables infinite resources if true.|
|`one_hit_ko`|true|Value determined from pre-match settings; enables OHKO if true.|
|`burst_enabled`|true|Value determined from pre-match settings; enables bursting if true.|
|<p class="nowrap">`always_perfect_parry`</p>|true|Value determined from pre-match settings; causes every block to parry regardless of timing if true.|
|`blocked_last_hit`|true|True if you successfully blocked the opponent's last move.|
||||
|`trail_hp`|MAX_HEALTH|Must be int. N/A|
|`hp`|0|Must be int. N/A|
|`super_meter`|0|Must be int. N/A|
|`supers_available`|0|Must be int. N/A|
|`combo_proration`|0|Must be int. N/A|
||||
|<p class="nowrap">`parried_last_state`</p>|false|Most likely set to true if this fighter parried the opponent's last move.|
|<p class="nowrap">`initiative_effect`</p>|false|N/A|
||||
|`burst_meter`|0|Must be int. N/A|
|`bursts_available`|0|Must be int. N/A|
||||
|`busy_interrupt`|false|N/A|
|<p class="nowrap">`any_available_actions`</p>|false|N/A|
||||
|`state_changed`|false|N/A|
|`on_the_ground`|false|True if the fighter is on the ground.|
|`nudge_amount`|"1.0"|N/A|
||||
|`feints`|2|Likely tied to the number of free cancels this fighter can use out of neutral.|
||||
|`current_nudge`|{"x":"0","y":"0"}|N/A|
|`current_di`|{"x":"0","y":"0"}|Current direct input vector for this fighter.|
|`last_vel`|{"x":"0","y":"0"}|Likely the last recorded velocity for this fighter.|
|`last_aerial_vel`|{"x":"0","y":"0"}|Likely the last recorded aerial velocity for this fighter.|
||||
|`combo_moves_used`|{}|N/A|
||||
|`reverse_state`|false|A boolean value likely used to track if the move's "reverse" slider is being used.|
|`ghost_reverse`|false|A boolean value likely used to track if the move should be reversed for the prediction ghost. Would'nt recommend touching this value.|
||||
|<p class="nowrap">`nudge_distance_left`</p>|0|N/A|
||||
|`can_nudge`|false|Likely a boolean value for if this fighter can nudge.|
|`parried`|false|N/A|
||||
|`initiative`|false|True if this fighter has initiative.|
|`aura_particle`|null|N/A|
||||
|`feinting`|false|True if this fighter is feinting.|
||||
|`last_action`|0|N/A|
||||
|`stance`|"Normal"|Current stance for the fighter.|
||||
|`parried_hitboxes`|[]|N/A|
||||
|<p class="nowrap">`grounded_hits_taken`</p>|0|N/A|
||||
|`throw_pos_x`|16|Likely tied to the X distance this fighter will throw the opponent after a grab.|
|`throw_pos_y`|-5|Likely tied to the Y distance this fighter will throw the opponent after a grab.|
||||
|`combo_damage`|0|Likely tracks the amount of damage this fighter has taken during a combo.|
|`hitlag_applied`|0|N/A|
|`forfeit_ticks`|0|N/A|
||||
|`lowest_tick`|0|N/A|

##Enumerations

There are no enumerated types for this class.

##Constants

|Constant|Value|Description|
|:-----:|:-----:|:-----:|
|MAX_STALES|15|N/A|
|MIN_STALE_MODIFIER|"0.2"|N/A|
||||
|DAMAGE_SUPER_SCALE_DIVISOR|1|Likely the number that super gain from dealing damage is divided by.|
|DAMAGE_TAKEN_SUPER_GAIN_DIVISOR|3|Likely the number that super gain from taking damage is divided by.|
|HITLAG_COLLISION_TICKS|4|N/A|
|PROJECTILE_PERFECT_PARRY_WINDOW|3|Likely the number of ticks that this fighter is alloted to perfectly parry a projectile.|
|BURST_ON_DAMAGE_AMOUNT|5|N/A|
||||
|COUNTER_HIT_ADDITIONAL_HITLAG_FRAMES|3|N/A|
||||
|MAX_GROUNDED_HITS|7|N/A|
||||
|PARRY_CHIP_DIVISOR|3|N/A|
|PARRY_KNOCKBACK_DIVISOR|"3"|N/A|
||||
|P1_COLOR|Color("aca2ff")|Likely the color player 1 will display as to the player.|
|P2_COLOR|Color("aca2ff")|Likely the color player 2 will display as to the player.|
||||
|GUTS_REDUCTIONS|{"1":"1", "0.70":"0.90", "0.60":"0.80", "0.50":"0.70", "0.40":"0.60", "0.30":"0.55", "0.20":"0.52", "0.10":"0.50", }|N/A|
||||
|MAX_GUTS|10|N/A|
||||
|MAX_DI_COMBO_ENHANCMENT|15|Likely the max coefficient for directional input influence.|
||||
|MAX_BURSTS|1|Likely the max amount of bursts this fighter can use from one burst meter.|
|BURST_BUILD_SPEED|4|Likely the speed at which the burst meter builds.|
|MAX_BURST_METER|1500|Likely the integer maximum for this fighter's burst meter.|
|START_BURSTS|1|Likely the amount of bursts this fighter starts with.|
||||
|MAX_SUPER_METER|125|Likely the integer maximum for this fighter's super meter.|
|MAX_SUPERS|9|Likely the amount of super levels this fighter can store.|
|VEL_SUPER_GAIN_DIVISOR|4|N/A|
||||
|NUDGE_DISTANCE|20|N/A|
||||
|PARRY_METER|50|N/A|
|METER_GAIN_MODIFIER|"1.0"|N/A|

##Methods

<div class="spacer"></div>

`init(pos = null)`

Init function

Serves to handle fighter properties when lobby options are changed; i.e. if one hit K.O. is enabled.

returns `null`

<div class="spacer"></div>

`apply_style(style)`

No information on this function. Does nothing if not using the Steam release of YOMI Hustle.

returns `null`

<div class="spacer"></div>

`reset_color()`

Resets the shader parameters for both fighters.

Returns `null`

<div class="spacer"></div>

`reset_aura()`

Resets the "aura" for both fighters. (???)

Returns `null`

<div class="spacer"></div>

`reset_style()`

Resets the "style" for both fighters. (???)

Returns `null`

<div class="spacer"></div>

`reapply_style()`

Reapplies "style" (???)

Returns `null`

<div class="spacer"></div>

`start_super()`

Emits the `super_started` signal.

Returns `null`

<div class="spacer"></div>

`change_stance_to(stance)`

Changes the fighter's stance to a string supplied to the `stance` argument.

Returns `null`

<div class="spacer"></div>

`show_you_label()`

Shows the "you" label.

Returns `null`

<div class="spacer"></div>

`is_you()`

Returns your player I.D. if you are in a multiplayer match.

Returns `Network.player_id, false`

<div class="spacer"></div>

`_ready()`

Ready function

Sets the fighter's sprite animation to `"Wait"`, does extra work with the state variables array and a couple of signals; please document further.

Returns `null`

<div class="spacer"></div>

`on_state_changed(states_stack)`

Likely runs whenever this fighter changes states. Does nothing by default.

Returns `null`

<div class="spacer"></div>

`on_got_hit()`

Runs whenever this fighter gets hit. Does nothing by default.

Returns `null`

<div class="spacer"></div>

`gain_burst_meter(amount = null)`

Does nothing if bursts arent enabled; adds `BURST_BUILD_SPEED` to the burst meter if `amount` is not defined; else, adds `amount` to the burst meter; if the burst meter is over the limit, gain a burst.

Returns `null`

<div class="spacer"></div>

`copy_to()`

N/A

Returns `null`

<div class="spacer"></div>

`gain_burst()`

Handles logic for gaining a burst; gives a burst if the fighter has not reached their limit on bursts.

Returns `null`

<div class="spacer"></div>

`use_burst()`

Decrements the amount of bursts available by 1. Does nothing if `infinite_resources` is set to true.

Returns `null`

<div class="spacer"></div>

`use_burst_meter(amount)`

Decrements the burst meter by `amount`.

Returns `null`

<div class="spacer"></div>

`use_super_bar()`

Removes 1 super level from the fighter; if the fighter does not have a super level, set the bar to empty. Does nothing if `infinite_resources` is set to true.

Returns `null`

<div class="spacer"></div>

`use_super_meter(amount)`

Removes `amount` from the fighter's super meter; if the fighter does not have enough super meter, the bar is set to empty. Does nothing if `infinite_resources` is set to true.

Returns `null`

<div class="spacer"></div>

`stack_move_in_combo(move_name)`

N/A

Returns `null`

<div class="spacer"></div>

`gain_super_meter(amount)`

Adds post-stale math `amount` to the fighter's super meter.

Returns `null`

<div class="spacer"></div>

`combo_stale_meter(meter:int)`

Handles combo staling math.

Returns `null`

<div class="spacer"></div>

`update_data()`

Updates the `data` variable.

Returns `null`

<div class="spacer"></div>

`get_playback_input`

N/A

Returns `null`

<div class="spacer"></div>

`reset_combo()`

Resets this fighter's combo.

Returns `null`

<div class="spacer"></div>

`incr_combo()`

Increments this fighter's combo counter by 1.

Returns `null`

<div class="spacer"></div>

`is_colliding_with_opponent`

Returns true if this fighter is colliding with the opponent, or is grabbed (?).

Returns `true, false`

<div class="spacer"></div>

`thrown_by(hitbox:ThrowBox)`

N/A

Returns `null`

<div class="spacer"></div>

`_process(_delta)`

N/A

Returns `null`

<div class="spacer"></div>

`debug_text()`

Debug function. N/A

Returns `null`

<div class="spacer"></div>

`has_armor()`

Returns false by default. Probably used for super armor mechanics.

Returns `false`

<div class="spacer"></div>

`launched_by(hitbox)`

N/A

Returns `null`

<div class="spacer"></div>

`hit_by(hitbox)`

N/A

Returns `null`

<div class="spacer"></div>

`set_throw_position(x:int, y:int)`

Changes the throw position of this fighter's throw.

Returns `null`

<div class="spacer"></div>

`take_damage(damage:int, minimum = 0)`

Causes your fighter to take damage, calculates burst gain from damage taken, and gives your opponent super meter based on the damage taken.

Returns `null`

<div class="spacer"></div>

`get_guts()`

N/A

Returns `current_guts`

<div class="spacer"></div>

`get_combo_stale(count)`

N/A

Returns `mod`

<div class="spacer"></div>

`guts_stale_damage(damage:int)`

N/A

Returns `damage`

<div class="spacer"></div>

`can_parry_hitbox(hitbox)`

N/A

Returns `true, false`

<div class="spacer"></div>

`set_color(color:Color)`

Sets the color of this fighter.

Returns `null`

<div class="spacer"></div>

`release_opponent()`

If the opponent is grabbed, sets their state to the falling state.

Returns `null`

<div class="spacer"></div>

`process_extra(extra)`

N/A

Returns `null`

<div class="spacer"></div>

`refresh_air_movements()`

Sets the number of air options for this fighter back to maximum.

Returns `null`

<div class="spacer"></div>

`refresh_feints()`

Sets the number of free cancels for this fighter back to maximum.

Returns `null`

<div class="spacer"></div>

`clean_parried_hitboxes()`

N/A

Returns `null`

<div class="spacer"></div>

`get_opponent_dir()`

Returns the difference between your fighter's position and the opponent's position.

Returns `Utils.int_sign(opponent.get_pos().x - get_pos().x)`

<div class="spacer"></div>

`get_advantage()`

Returns information regarding frame advantage.

Returns `advantage`

<div class="spacer"></div>

`set_lowest_tick()`

N/A

Returns `null`

<div class="spacer"></div>

`tick_before()`

N/A

Returns `null`

<div class="spacer"></div>

`toggle_quit_graphic(on = null)`

Toggles the 'QUITTER" graphic; also handles the sound for quitters. Shame on them.

Returns `null`

<div class="spacer"></div>

`tick()`

N/A

Returns `null`

<div class="spacer"></div>

`set_ghost_colors()`

Responsible for handling the colors of the prediction ghosts.

Returns `null`

<div class="spacer"></div>

`set_facing(facing:int, force = false)`

Causes the fighter to face a set direction based on `facing`, unless `reverse_state` is true. Forcibly causes the fighter to face a set direction regardless of `reverse_state` if `force` is set to true.

Returns `null`

<div class="spacer"></div>

`update_facing()`

Updates the direction this fighter is facing, based on the opponent's location.

Returns `null`

<div class="spacer"></div>

`on_state_interruptable(state)`

N/A

Returns `null`

<div class="spacer"></div>

`on_state_hit_cancellable(state)`

N/A

Returns `null`

<div class="spacer"></div>

`on_action_selected(action, data, extra)`

Called whenever the player selects an action for this fighter.

Returns `null`

<div class="spacer"></div>

`forfeit()`

Sets `will_forfeit` to true.

Returns `null`

<div class="spacer"></div>

`_draw()`

Does nothing by default. N/A

Returns `null`

<div class="spacer"></div>

##Signals

`action_selected(action, data)`

N/A

`super_started()`

N/A

`parried()`

N/A

`undo()`

N/A

`forfeit()`

N/A

##Credits

Info contributed by [D00dlenoodles](https://rmld00dlenoodles.github.io/YOMIDoku/about/#contact-information)

##Source

??? abstract "BaseChar.gd"
	```gd
	extends BaseObj

	class_name Fighter

	signal action_selected(action, data)
	signal super_started()
	signal parried()
	signal undo()
	signal forfeit()


	var MAX_HEALTH = 1000













	const MAX_STALES = 15
	const MIN_STALE_MODIFIER = "0.2"

	const DAMAGE_SUPER_GAIN_DIVISOR = 1
	const DAMAGE_TAKEN_SUPER_GAIN_DIVISOR = 3
	const HITLAG_COLLISION_TICKS = 4
	const PROJECTILE_PERFECT_PARRY_WINDOW = 3
	const BURST_ON_DAMAGE_AMOUNT = 5

	const COUNTER_HIT_ADDITIONAL_HITLAG_FRAMES = 3

	const MAX_GROUNDED_HITS = 7

	const PARRY_CHIP_DIVISOR = 3
	const PARRY_KNOCKBACK_DIVISOR = "3"

	const P1_COLOR = Color("aca2ff")
	const P2_COLOR = Color("ff7a81")

	const GUTS_REDUCTIONS = {
		"1":"1", 


		"0.70":"0.90", 
		"0.60":"0.80", 
		"0.50":"0.70", 
		"0.40":"0.60", 
		"0.30":"0.55", 
		"0.20":"0.52", 
		"0.10":"0.50", 
	}

	const MAX_GUTS = 10

	const MAX_DI_COMBO_ENHANCMENT = 15

	const MAX_BURSTS = 1
	const BURST_BUILD_SPEED = 4
	const MAX_BURST_METER = 1500
	const START_BURSTS = 1

	const MAX_SUPER_METER = 125
	const MAX_SUPERS = 9
	const VEL_SUPER_GAIN_DIVISOR = 4


	const NUDGE_DISTANCE = 20

	const PARRY_METER = 50
	const METER_GAIN_MODIFIER = "1.0"

	export  var num_air_movements = 2

	export (Texture) var character_portrait

	onready var you_label = $YouLabel
	onready var actionable_label = $ActionableLabel
	onready var quitter_label = $"%QuitterLabel"

	var input_state = InputState.new()

	var color = Color.white

	export (PackedScene) var player_info_scene
	export (PackedScene) var player_extra_params_scene

	export  var damage_taken_modifier = "1.0"

	export  var num_feints = 2

	var opponent

	var queued_action = null
	var queued_data = null
	var queued_extra = null

	var dummy_interruptable = false

	var game_over = false
	var forfeit = false
	var will_forfeit = false

	var applied_style = null
	var is_color_active = false
	var is_aura_active = false
	var is_style_active = null

	var ivy_effect = false

	var colliding_with_opponent = true

	var air_movements_left = 0

	var action_cancels = {
	}

	var ghost_ready_tick = null
	var ghost_ready_set = false
	var got_parried = false

	var di_enabled = true
	var turbo_mode = false
	var infinite_resources = false
	var one_hit_ko = false
	var burst_enabled = true
	var always_perfect_parry = false
	var blocked_last_hit = false

	var trail_hp:int = MAX_HEALTH
	var hp:int = 0
	var super_meter:int = 0
	var supers_available:int = 0
	var combo_proration:int = 0

	var parried_last_state = false
	var initiative_effect = false

	var burst_meter:int = 0
	var bursts_available:int = 0

	var busy_interrupt = false
	var any_available_actions = true

	var state_changed = false
	var on_the_ground = false
	var nudge_amount = "1.0"

	var feints = 2


	var current_nudge = {
		"x":"0", 
		"y":"0", 
	}

	var current_di = {
		"x":"0", 
		"y":"0", 
	}

	var last_vel = {
		"x":"0", 
		"y":"0", 
	}

	var last_aerial_vel = {
		"x":"0", 
		"y":"0", 
	}

	var combo_moves_used = {}

	var reverse_state = false
	var ghost_reverse = false

	var nudge_distance_left = 0

	var can_nudge = false
	var parried = false

	var initiative = false
	var aura_particle = null

	var feinting = false

	var last_action = 0

	var stance = "Normal"

	var parried_hitboxes = []

	var grounded_hits_taken = 0

	var throw_pos_x = 16
	var throw_pos_y = - 5

	var combo_damage = 0
	var hitlag_applied = 0
	var forfeit_ticks = 0

	var lowest_tick = 0

	class InputState:
		var name
		var data

	func init(pos = null):
		.init(pos)
		if not is_ghost:
			Network.player_objects[id] = self
		feints = num_feints
		if one_hit_ko:
			MAX_HEALTH = 1
		hp = MAX_HEALTH
		game_over = false
		show_you_label()
		if burst_enabled:
			for i in range(START_BURSTS):
				gain_burst()
		for state in state_machine.get_children():
			if state is CharacterState:
				for category in state.interrupt_from:
					if not action_cancels.has(category):
						action_cancels[category] = []
					if not (state in action_cancels[category]):
						action_cancels[category].append(state)
		if infinite_resources:
			supers_available = MAX_SUPERS
			super_meter = MAX_SUPER_METER

	func apply_style(style):
		if not SteamYomi.STARTED:
			return 
		if style != null and not is_ghost:
			is_color_active = true
			is_style_active = true
			applied_style = style
			if Global.enable_custom_colors and style.has("character_color") and style.character_color != null:
				set_color(style.character_color)
				Custom.apply_style_to_material(style, sprite.get_material())
			if Global.enable_custom_particles and not is_ghost and style.show_aura and style.has("aura_settings"):
				reset_aura()
				is_aura_active = true
				aura_particle = preload("res://fx/CustomTrailParticle.tscn").instance()
				particles.add_child(aura_particle)
				aura_particle.load_settings(style.aura_settings)
				aura_particle.position = hurtbox_pos_float()
				aura_particle.start_emitting()
				if aura_particle.show_behind_parent:
					aura_particle.z_index = - 1
			if style.has("hitspark"):
				custom_hitspark = load(Custom.hitsparks[style.hitspark])
				for hitbox in hitboxes:
					hitbox.HIT_PARTICLE = custom_hitspark





	func reset_color():
		is_color_active = false
		sprite.get_material().set_shader_param("color", P1_COLOR if id == 1 else P2_COLOR)
		sprite.get_material().set_shader_param("use_outline", false)

	func reset_aura():
		is_aura_active = false
		if is_instance_valid(aura_particle):
			aura_particle.queue_free()
		aura_particle = null

	func reset_style():
		reset_color()
		reset_aura()
		is_style_active = false

	func reapply_style():
		apply_style(applied_style)

	func start_super():
		emit_signal("super_started")

	func change_stance_to(stance):
		self.stance = stance

	func show_you_label():
		if is_you():
			you_label.show()

	func is_you():
		if Network.multiplayer_active:
			return id == Network.player_id
		return false

	func _ready():
		sprite.animation = "Wait"
		state_variables.append_array(
			["current_di", "current_nudge", "feinting", "feints", "lowest_tick", "is_color_active", "blocked_last_hit", "combo_proration", "state_changed", "nudge_amount", "initiative_effect", "reverse_state", "combo_moves_used", "parried_last_state", "initiative", "last_vel", "last_aerial_vel", "trail_hp", "always_perfect_parry", "parried", "got_parried", "parried_this_frame", "grounded_hits_taken", "on_the_ground", "hitlag_applied", "combo_damage", "burst_enabled", "di_enabled", "turbo_mode", "infinite_resources", "one_hit_ko", "dummy_interruptable", "air_movements_left", "super_meter", "supers_available", "parried", "parried_hitboxes", "burst_meter", "bursts_available"]
		)
		add_to_group("Fighter")
		connect("got_hit", self, "on_got_hit")
		state_machine.connect("state_changed", self, "on_state_changed")

	func on_state_changed(states_stack):

		pass

	func on_got_hit():
		pass

	func gain_burst_meter(amount = null):
		if not burst_enabled:
			return 
		if bursts_available < MAX_BURSTS:
			burst_meter += BURST_BUILD_SPEED if amount == null else amount
			if burst_meter > MAX_BURST_METER:
				gain_burst()

	func copy_to(f):
		.copy_to(f)
		f.update_data()
		f.set_facing(get_facing_int(), true)
		f.update_data()
		

	func gain_burst():
		if bursts_available < MAX_BURSTS:
			bursts_available += 1
			burst_meter = 0

	func use_burst():
		if infinite_resources:
			return 
		bursts_available -= 1
		refresh_air_movements()

	func use_burst_meter(amount):
		if infinite_resources:
			return 
		if bursts_available > 0:
			bursts_available = 0
			burst_meter = MAX_BURST_METER
		burst_meter -= amount

	func use_super_bar():
		if infinite_resources:
			return 
		supers_available -= 1
		if supers_available < 0:
			supers_available = 0
			super_meter = 0

	func use_super_meter(amount):
		if infinite_resources:
			return 
		super_meter -= amount
		if super_meter < 0:
			if supers_available > 0:
				super_meter = MAX_SUPER_METER + super_meter
				use_super_bar()
			else :
				super_meter = 0

	func stack_move_in_combo(move_name):
		if combo_moves_used.has(move_name):
			combo_moves_used[move_name] += 1
		else :
			combo_moves_used[move_name] = 1

	func gain_super_meter(amount):
		amount = combo_stale_meter(amount)
		super_meter += amount
		if super_meter >= MAX_SUPER_METER:
			if supers_available < MAX_SUPERS:
				super_meter -= MAX_SUPER_METER
				supers_available += 1
			else :
				super_meter = MAX_SUPER_METER
				
	func combo_stale_meter(meter:int):
		var staling = get_combo_stale(combo_count)
		return fixed.round(fixed.mul(fixed.mul(str(meter), staling), METER_GAIN_MODIFIER))
		
	func update_data():
		data = get_data()
		obj_data = data["object_data"]
		data["state_data"] = {
			"state":current_state().state_name, 
			"frame":current_state().current_tick, 
			"combo count":combo_count, 
		}

	func get_playback_input():
		if ReplayManager.playback:
			if get_frames().has(current_tick):
				return get_frames()[current_tick]

	func get_global_throw_pos():
		var pos = get_pos()
		pos.x += throw_pos_x * get_facing_int()
		pos.y += throw_pos_y
		return pos

	func reset_combo():
		combo_count = 0
		combo_damage = 0
		combo_proration = 0
		combo_moves_used = {}
		opponent.grounded_hits_taken = 0
		opponent.trail_hp = opponent.hp

	func incr_combo():
		combo_count += 1

	func is_colliding_with_opponent():
		return (colliding_with_opponent or (current_state() is CharacterHurtState and (hitlag_applied - hitlag_ticks) < HITLAG_COLLISION_TICKS) and current_state().state_name != "Grabbed")

	func thrown_by(hitbox:ThrowBox):
		emit_signal("got_hit")
		state_machine._change_state("Grabbed")

	func hitbox_from_name(hitbox_name):
			var hitbox_props = hitbox_name.split("_")
			var obj_name = hitbox_props[0]
			var hitbox_id = int(hitbox_props[ - 1])
			var obj = objs_map[obj_name]
			if obj:
				return objs_map[obj_name].hitboxes[hitbox_id]

	func _process(_delta):
		update()
		if invulnerable:
			if (Global.current_game.real_tick / 1) % 2 == 0:
				var transparent = color
				self_modulate.a = 0.5

			else :
				self_modulate.a = 1.0

		else :
			self_modulate.a = 1.0
		if is_instance_valid(aura_particle):
			aura_particle.visible = Global.enable_custom_particles
			aura_particle.position = hurtbox_pos_float()
			aura_particle.facing = get_facing_int()
		
		if is_style_active:
			if applied_style and not is_color_active and Global.enable_custom_colors:
				apply_style(applied_style)
			if applied_style and not is_aura_active and Global.enable_custom_particles:
				apply_style(applied_style)
		if is_color_active and not Global.enable_custom_colors:
			reset_color()
		if is_aura_active and not Global.enable_custom_particles:
			reset_aura()

	func debug_text():
		.debug_text()
		debug_info(
			{
				"lowest_tick":lowest_tick, 
				"initiative":initiative, 
			}
		)

	func has_armor():
		return false

	func launched_by(hitbox):


		hitlag_ticks = hitbox.victim_hitlag + (COUNTER_HIT_ADDITIONAL_HITLAG_FRAMES if hitbox.counter_hit else 0)
		hitlag_applied = hitlag_ticks
		
		if objs_map.has(hitbox.host):
			var host = objs_map[hitbox.host]
			if host.hitlag_ticks < hitbox.hitlag_ticks:
				host.hitlag_ticks = hitbox.hitlag_ticks
		
		if hitbox.rumble:
			rumble(hitbox.screenshake_amount, hitbox.victim_hitlag if hitbox.screenshake_frames < 0 else hitbox.screenshake_frames)
		
		nudge_amount = hitbox.sdi_modifier
		
		if hitbox.ignore_armor or not has_armor():
			var state
			if is_grounded():
				state = hitbox.grounded_hit_state
			else :
				state = hitbox.aerial_hit_state

			if state == "HurtGrounded":
				grounded_hits_taken += 1
				if grounded_hits_taken >= MAX_GROUNDED_HITS:
					state = "HurtAerial"
					grounded_hits_taken = 0

			state_machine._change_state(state, {"hitbox":hitbox})
			if hitbox.disable_collision:
				colliding_with_opponent = false

			busy_interrupt = true
			can_nudge = true
					
			if opponent.combo_count == 0:
				opponent.combo_proration = hitbox.damage_proration

			var host = objs_map[hitbox.host]
			var projectile = not host.is_in_group("Fighter")

			if not projectile:
				refresh_feints()
				opponent.refresh_feints()

			if hitbox.increment_combo:
				opponent.incr_combo()

		emit_signal("got_hit")
		take_damage(hitbox.damage, hitbox.minimum_damage)
		state_tick()

	func hit_by(hitbox):
		if parried:
			return 
		if hitbox.name in parried_hitboxes:
			return 
		if not hitbox.hits_otg and is_otg():
			return 
		if hitbox.throw and not is_otg():
			return thrown_by(hitbox)
			
		if not can_parry_hitbox(hitbox):
			
			match hitbox.hitbox_type:
				Hitbox.HitboxType.Normal:
					launched_by(hitbox)
				Hitbox.HitboxType.Flip:
					set_facing(get_facing_int() * - 1, true)
					var vel = get_vel()
					set_vel(fixed.mul(vel.x, "-1"), vel.y)
					for hitbox in hitboxes:
						hitbox.facing = get_facing()
						pass
					emit_signal("got_hit")
					take_damage(hitbox.damage, hitbox.minimum_damage)
				Hitbox.HitboxType.ThrowHit:
					emit_signal("got_hit")
					take_damage(hitbox.damage, hitbox.minimum_damage)
					opponent.incr_combo()
		else :
			opponent.got_parried = true
			
			var host = objs_map[hitbox.host]
			var projectile = not host.is_in_group("Fighter")
			var perfect_parry
			if not projectile:
				perfect_parry = always_perfect_parry or opponent.current_state().feinting or opponent.feinting or (initiative and not blocked_last_hit) or parried_last_state
				opponent.feinting = false
				opponent.current_state().feinting = false
			else :

				perfect_parry = always_perfect_parry or parried_last_state or (current_state().current_tick < PROJECTILE_PERFECT_PARRY_WINDOW and host.has_projectile_parry_window)
			if perfect_parry:
				parried_last_state = true
			else :
				blocked_last_hit = true
			
			
			parried = true

			hitlag_ticks = 0
			parried_hitboxes.append(hitbox.name)
			var particle_location = current_state().get("particle_location")
			particle_location.x *= get_facing_int()
			
			if not particle_location:
				particle_location = hitbox.get_overlap_center_float(hurtbox)
			var parry_meter = PARRY_METER if hitbox.parry_meter_gain == - 1 else hitbox.parry_meter_gain
			
			current_state().parry(perfect_parry)
			if not perfect_parry:
				take_damage(hitbox.damage / PARRY_CHIP_DIVISOR)
				apply_force_relative(fixed.div(hitbox.knockback, fixed.mul(PARRY_KNOCKBACK_DIVISOR, "-1")), "0")
				gain_super_meter(parry_meter / 3)
				opponent.gain_super_meter(parry_meter / 3)
				if not projectile:
					current_state().anim_length = opponent.current_state().anim_length
					current_state().endless = opponent.current_state().endless
					current_state().iasa_at = opponent.current_state().iasa_at



				spawn_particle_effect(preload("res://fx/FlawedParryEffect.tscn"), get_pos_visual() + particle_location)
				parried = false
				play_sound("Block")
				play_sound("Parry")
			else :
				spawn_particle_effect(preload("res://fx/ParryEffect.tscn"), get_pos_visual() + particle_location)
				gain_super_meter(parry_meter)
				play_sound("Parry2")
				play_sound("Parry")
				emit_signal("parried")

	func set_throw_position(x:int, y:int):
		throw_pos_x = x
		throw_pos_y = y

	func take_damage(damage:int, minimum = 0):
		if opponent.combo_count == 0:
			trail_hp = hp
		if damage == 0:
			return 
		gain_burst_meter(damage / BURST_ON_DAMAGE_AMOUNT)
		damage = Utils.int_max(guts_stale_damage(combo_stale_damage(damage)), 1)
		damage = Utils.int_max(damage, minimum)
		hp -= damage
		opponent.combo_damage += damage
		opponent.gain_super_meter(damage / DAMAGE_SUPER_GAIN_DIVISOR)
		gain_super_meter(damage / DAMAGE_TAKEN_SUPER_GAIN_DIVISOR)
		if hp < 0:
			hp = 0

	func get_guts():
		var current_guts = "1"
		for level in GUTS_REDUCTIONS:
			var hp_level = fixed.div(str(hp), str(MAX_HEALTH))
			if fixed.le(hp_level, level):
				current_guts = GUTS_REDUCTIONS[level]
		return current_guts

	func get_combo_stale(count):
		var ratio = fixed.div(fixed.sub(str(MAX_STALES), str(Utils.int_min(count, MAX_STALES))), str(MAX_STALES))
		var mod = fixed.mul(fixed.sub("1", MIN_STALE_MODIFIER), fixed.powu(ratio, 2))
		mod = fixed.add(mod, MIN_STALE_MODIFIER)
		return mod

	func guts_stale_damage(damage:int):
		var guts = get_guts()
		damage = fixed.round(fixed.mul(str(damage), guts))
		return damage

	func combo_stale_damage(damage:int):
		var staling = get_combo_stale(Utils.int_max(opponent.combo_count + (opponent.combo_proration if opponent.combo_count > 1 else 0) - 1, 0))
		return fixed.round(fixed.mul(str(damage), staling))

	func can_parry_hitbox(hitbox):
		if not current_state() is ParryState:
			return false
		if hitbox.hitbox_type == Hitbox.HitboxType.Flip:
			return false
		return current_state().can_parry_hitbox(hitbox)

	func set_color(color:Color):
		if color != null:
			sprite.get_material().set_shader_param("color", color)
			self.color = color

	func release_opponent():
		if opponent.current_state().state_name == "Grabbed":
			opponent.change_state("Fall")

	func process_extra(extra):
		if "DI" in extra:
			if di_enabled:
				var di = extra["DI"]
				current_nudge = xy_to_dir(di.x, di.y, str(NUDGE_DISTANCE))
				current_di = xy_to_dir(di.x, di.y, fixed.add("1.0", fixed.mul("1.0", fixed.div(str(Utils.int_min(MAX_DI_COMBO_ENHANCMENT, opponent.combo_count)), "5"))))
			else :
				current_di = FixedVec2String.new(0, 0)
		if "reverse" in extra:
			reverse_state = extra["reverse"]
			if reverse_state:
				ghost_reverse = true
		if "feint" in extra:
			feinting = extra.feint
			if feinting:
				feints -= 1
		else :
			feinting = false

	func refresh_air_movements():
		air_movements_left = num_air_movements

	func refresh_feints():
		feints = num_feints

	func clean_parried_hitboxes():


		if not parried_hitboxes:
			return 
		var hitboxes_to_refresh = []
		for hitbox_name in parried_hitboxes:
			var hitbox = hitbox_from_name(hitbox_name)
			if hitbox:
				if not hitbox.enabled or not hitbox.active:
					hitboxes_to_refresh.append(hitbox)

		for hitbox in hitboxes_to_refresh:
			parried_hitboxes.erase(hitbox.name)

	func get_opponent_dir():
		return Utils.int_sign(opponent.get_pos().x - get_pos().x)

	func get_advantage():
		if opponent == null:
			return true

		var minus_modifier = 0
		var advantage = (opponent and opponent.lowest_tick <= lowest_tick) or parried_last_state


		if state_interruptable and opponent.state_interruptable:
			advantage = true
		if current_state().state_name == "WhiffInstantCancel" or (previous_state() and previous_state().state_name == "WhiffInstantCancel" and current_state().has_hitboxes):
			advantage = false
		if opponent.current_state().state_name == "WhiffInstantCancel" or (opponent.previous_state() and opponent.previous_state().state_name == "WhiffInstantCancel" and opponent.current_state().has_hitboxes):
			advantage = false
		return advantage

	func set_lowest_tick(tick):
		if lowest_tick == null or tick < lowest_tick:
			lowest_tick = tick

	func update_advantage():
		var new_adv = get_advantage()
		if new_adv and not initiative:
			initiative_effect = true
		initiative = new_adv

	func tick_before():
		if queued_action == "Forfeit":
			if forfeit:
				queued_action = "Continue"
		
		dummy_interruptable = false
		clean_parried_hitboxes()
		busy_interrupt = false
		update_grounded()
		if ReplayManager.playback:
			var input = get_playback_input()
			if input:
				queued_action = input["action"]
				queued_data = input["data"]
				queued_extra = input["extra"]

				if queued_action == "Forfeit":

					forfeit = true
					Global.current_game.forfeit(id)
		else :
			if queued_action:

				if queued_action == "Undo":
					queued_action = null
					queued_data = null
					return 
				if queued_action == "Forfeit":
					forfeit = true

				if not is_ghost:
					ReplayManager.frames[id][current_tick] = {
						"action":queued_action, 
						"data":queued_data, 
						"extra":queued_extra, 
					}
		var feinted_last = feinting
		var pressed_feint = false
		if queued_extra:
			process_extra(queued_extra)
			pressed_feint = feinting
		if queued_action:
			if queued_action in state_machine.states_map:

				if feinted_last:
					var particle_pos = get_hurtbox_center_float()
					spawn_particle_effect(preload("res://fx/FeintEffect.tscn"), particle_pos)
				state_machine._change_state(queued_action, queued_data)
				if pressed_feint:
					feinting = true
					current_state().feinting = true
		queued_action = null
		queued_data = null
		queued_extra = null
		lowest_tick = current_state().current_real_tick

	func toggle_quit_graphic(on = null):
		if on == null:
			quitter_label.visible = not quitter_label.visible
			if quitter_label.visible:
				play_sound("QuitterSound")
		else :
			quitter_label.visible = on
			if on:
				play_sound("QuitterSound")

	func tick():
		if hitlag_ticks > 0:
			if can_nudge:
				if fixed.round(fixed.mul(fixed.vec_len(current_nudge.x, current_nudge.y), "100.0")) > 1:
					current_nudge = fixed.vec_mul(current_nudge.x, current_nudge.y, nudge_amount)
					spawn_particle_effect(preload("res://fx/NudgeIndicator.tscn"), Vector2(get_pos().x, get_pos().y + hurtbox.y), Vector2(current_di.x, current_di.y).normalized())
					move_directly(current_nudge.x, current_nudge.y if not is_grounded() else "0")
				can_nudge = false
			hitlag_ticks -= 1
			if hitlag_ticks == 0:
				if state_hit_cancellable:
					state_interruptable = true
					can_nudge = false
		else :
			if parried:

				parried = false
				if current_state().get("parry_active"):
					current_state().parry_active = false
				var prev = previous_state()
				if prev and prev.get("parry_active"):
					prev.parry_active = false
			var minus_offset = 0 if id == 1 else 1
			state_tick()

			if state_hit_cancellable:
				state_interruptable = true
				can_nudge = false
			if not current_state() is ThrowState:
				chara.apply_pushback(get_opponent_dir())
			if is_grounded():
				refresh_air_movements()
			current_tick += 1
			if not (current_state().is_hurt_state) and not (opponent.current_state().is_hurt_state):
				var x_vel_int = chara.get_x_vel_int()
				if Utils.int_sign(x_vel_int) == Utils.int_sign(opponent.get_pos().x - get_pos().x):
					gain_super_meter(Utils.int_max(Utils.int_abs(x_vel_int) / VEL_SUPER_GAIN_DIVISOR, 1))
		
		

		if state_interruptable:
			update_grounded()
		gain_burst_meter()
		update_data()
		for particle in particles.get_children():
			particle.tick()
		any_available_actions = true
		last_vel = get_vel()
		if not is_grounded():
			last_aerial_vel = last_vel
		if not (previous_state() is ParryState) or not (current_state() is ParryState):
			parried_last_state = false

		if forfeit:
			forfeit_ticks += 1
		if forfeit and forfeit_ticks > 2:
			change_state("ForfeitExplosion")
			forfeit = false

	func set_ghost_colors():
		if not ghost_ready_set and (state_interruptable or dummy_interruptable):
			ghost_ready_set = true
			ghost_ready_tick = current_tick
			if opponent.ghost_ready_tick == null or opponent.ghost_ready_tick == ghost_ready_tick:
				set_color(Color.green)
				if opponent.current_state().interruptible_on_opponent_turn or opponent.feinting:
					opponent.ghost_ready_set = true
					opponent.set_color(Color.green)
			elif opponent.ghost_ready_tick < ghost_ready_tick:
				set_color(Color.orange)

	func set_facing(facing:int, force = false):
		if reverse_state and not force:
			facing *= - 1
		.set_facing(facing)

	func update_facing():
		if obj_data.position_x < opponent.obj_data.position_x:
			set_facing(1)
		elif obj_data.position_x > opponent.obj_data.position_x:
			set_facing( - 1)
		if initialized:
			update_data()

	func on_state_interruptable(state):
		if not dummy:
			state_interruptable = true
		else :
			dummy_interruptable = true

	func on_state_hit_cancellable(state):
		if not dummy:
			state_hit_cancellable = true

	func on_action_selected(action, data, extra):


		if you_label.visible:
			you_label.hide()
		queued_action = action
		queued_data = data
		queued_extra = extra
		state_interruptable = false
		state_hit_cancellable = false
		if action == "Undo":
			emit_signal("undo")


		emit_signal("action_selected", action, data, extra)

	func forfeit():
		will_forfeit = true

	func _draw():




		pass
	```