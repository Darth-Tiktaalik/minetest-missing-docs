These notes are for those wishing to port mobs redo mobs to voxelibre mcl_mobs

Voxelibre Mcl_mobs is a fork of mobs redo and appears mostly compatible 





[probably essential values when converting from mobs redo](#new-values-to-add-when-converting-from-mobs-redo) 


[mob spawning](#mob_spawning)

[spawning in biomes](#spawning-in-biomes)
   
   
   [spawning on structures](#spawning-on-structures)

<h5>new values to add when converting from mobs redo</h5>

appears to want registration in form of mcl_mobs.register_mob(), mostly uses values from mobs redo except that:

can_despawn is a value that can be true or false but one of these must be set to avoid nil value crash, also needs spawn_class string.

values for xp_min and xp_max that can (must?) be set, determines how many experience points drop when a mob is killed

Handy template to add to your preexisting mobs_redo mobs when converting them to mcl_mobs 

        xp_min = 1,
        xp_max = 1,
        can_despawn = true,
        spawn_class = "",


mcl_mobs.register_arrow() didn't have any obvious breaking changes from mobs redo when experimenting with zombies4test's spitter zombie.


<h5>Mob spawning</h5>
TODO: research if mcl_mobs or other voxelibre mod supports suppressing specific built in mobs, in my use case ensuring that zombies from mod fully replace mobs_mc zombies. There exists a non_spawn_specific function for mobs not meant to spawn in overworld that may be of use here.  

mainly governed by two functions(?)  


<h6>spawning in biomes</h6> is done via mcl_mobs.spawn_specific() and arguments are supplied in the order of mcl_mobs.spawn_specific(name, dimension, type_of_spawning, biomes, min_light, max_light, interval, chance, aoc, min_height, max_height, day_toggle, on_spawn, check_position)  




dimension here is meant in the sense of overworld, nether and end dimensions while type of spawn means whether it spawns on ground, water or lava.  

biomes are all listed in voxelibre's [mods/MAPGEN/mcl_biomes/init.lua](https://git.minetest.land/VoxeLibre/VoxeLibre/src/branch/master/mods/MAPGEN/mcl_biomes/init.lua)  

spawn_specific doesn't appear to support specifying an exact node type to spawn on.


<h6>spawning on structures</h6> is done via mcl_structures.register_structure_spawn()

It accepts at least the following values in a table:

name = string(determines what mob spawns, should be supplied as modname:mobname, e.g name = "zombies4test:doctorzombie",)

y_min = number & y_max = number  (coordinates)
	
 chance = number(spawn chance)
	
 interval = number 
	
 limit = number(maximum amount that can spawn)
	
 spawnon = string (what nodes of the structure mob spawns on, should be supplied as modname:nodename)


 For information on registering structures, refer to voxelibre's [MAPGEN/mcl_structures/API.md](https://git.minetest.land/VoxeLibre/VoxeLibre/src/branch/master/mods/MAPGEN/mcl_structures/API.md)

 







