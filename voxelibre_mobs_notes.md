Voxelibre Mcl_mobs is a fork of mobs redo and appears mostly compatible except some new values that cannot be omitted

can_despawn is a value that can be true or false but one of these must be set to avoid nil value crash, also needs spawn_class string

values for xp_min and xp_max that can (must?) be set, determines how many experience points drop when a mob is killed

appears to want registration in form of mcl_mobs.register_mob("zombies4test:survivorzombie", survivorzombie)

Mob spawning is mainly governed by two functions(?)


for spawning in biomes mcl_mobs:spawn_specific() and are supplied in the form of mcl_mobs:spawn_specific(name, dimension, type_of_spawning, biomes, min_light, max_light, interval, chance, aoc, min_height, max_height, day_toggle, on_spawn, check_position)

dimension here is meant in the sense of overworld, nether and end dimensions while type of spawn means whether it spawns on ground, water or lava.

biomes are all listed in mcl_mobs' spawning.lua file


For spawning on structures it appears to want  mcl_structures.register_structure_spawn()

It accepts at least the following values in a table:

name = string(determines what mob spawns, should be supplied as modname:mobname, e.g name = "zombies4test:doctorzombie",)
	name = "mobs_mc:pillager",
	y_min =number & y_max = number  (coordinates)
	chance = number(spawn chance)
	interval = number 
	limit =number(maximum amount that can spawn)
	spawnon = string (what nodes of the structure mob spawns on, should be supplied as modname:nodename)







Handy template to add to to mcl_mob defines

        xp_min = 1,
        xp_max = 1,
        can_despawn = true,
        spawn_class = "",

