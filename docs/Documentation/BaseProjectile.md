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

#BaseProjectile

In: res://projectile/BaseProjectile.gd

Inherits: BaseObj > BaseProjectile

##Description

Base class used for projectiles. This file mostly defines properties to be used by projectile state scripts, such as DefaultFireball.

##Properties

|Property|Default Value|Description|
|:-----:|:-----:|:-----:|
|`immunity_susceptible` | true | N/A|
|<p class="nowrap">`deletes_other_projectiles`</p> | true | Whether or not the projectile deletes other projectiles that collide with it.|

##Enumerations

<p>There are no enumerated types for this class.</p>

##Constants

<p>There are no constants for this class.</p>

##Methods

<div class="spacer"></div>

`disable()`

Removes the projectile from play. Note that this doesn't actually delete the projectile, but disables the sprite, hitboxes, and particles, rendering the projectile invisible and unable to interact with other objects.

returns `null`

<div class="spacer"></div>

##Signals

<p>There are no signals for this class.</p>

##Credits

Info contributed by [xColdxFusionx](https://rmld00dlenoodles.github.io/YOMIDoku/about/#attributions)

##Source

??? abstract "BaseProjectile.gd"
	```gd
	extends BaseObj

	class_name BaseProjectile

	export  var immunity_susceptible = true
	export  var deletes_other_projectiles = true

	func disable():
		sprite.hide()
		disabled = true
		for hitbox in get_active_hitboxes():
			hitbox.deactivate()
		stop_particles()
	```

