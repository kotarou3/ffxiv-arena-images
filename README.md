# FFXIV Arena Images

Renders of various in-game arenas applicable to FFXIV ultimate raiders. Useful
for creating pictures for guiding people's positions

## General
Scale is 50 pixels = 1 metre = 1 yalm

Some textures are wrong (mostly repeating floor textures), but floor markings
should be correct. Effects and skybox are not included

Wrong textures are probably an incomplete game export, or they're covered up by
effects in-game. I've no clue with game 3D stuff so I don't know how to fix it.
Let me (kota#7848) know if you know how

`*-cropped` files are arenas cropped to their "death walls" or boundaries.  
`*-no-background` files are arenas with most of the background embellishments
removed where applicable, but keeps any parts of the foreground arena even if
they're outside the "death walls"

## Specific comments
### UCoB
Arena radius: 22m

P1 (Twintania) and P2 (Nael) are probably useless due to the wrong textures issue

P3 and P4 (Bahamut) has transparent floors (which just reveals the skybox in-game),
which I've just left as-is. Feel free to fill the background in yourself

### UWU
Arena radius: 20m  
P3 shrunken radius: 16 & 12m

P1 (Garuda), P2 (Ifrit), P4 (LB phase) are probably useless due to the wrong
textures issue

P3 (Titan) shows the final state of the arena after its been shrunk twice. I
don't know how to show the other states/sizes of the arena

P5 (Ultima) has wrong floor textures. But the lines on the floor should be
correct, as well as the runes on the outside

### TEA
Arena radius: 20m

The grey circle on the P1 (Living Liquid), P2 (Brute Justice), and P4 (Perfect
Alexander) arenas is the "death circle" that normally glows purple ingame

P3 (Alexander Prime) has a transparent floor (which just reveals the skybox in-game),
which I've just left as-is. Feel free to fill the background in yourself

P4 (Perfect Alexander) technically has a transparent floor too, but it's fully
enclosed further at the bottom (so you can't see the skybox through it). The
version including the background shows the bottom of the enclosure, but the
no-background version shows the transparent floor

P.S. The floor textures all turned out surprisingly well for this fight. You
might also notice some tubes on the edge of the P2 arena not actually touching
the arena - likely just an oversight by the game developers

Trivia: As part of the P4 enrage sequence, the 8 radial white shafts beneath the
floor get pulled out and are turned by Alexander. This is how they appear in the
exported model of the arena, so to get an accurate non-enrage sequence arena they
have to be manually retracted ~7.36m (distance guessed and unchecked with ingame)

### DSU
P1/3 arena size: 44×44m
P2/4/5 arena radius: 21m

The arena seems to be massive compared to previous ultimates, with the full
foreground arena (before being limited in size by a death wall) being 36m in
radius

The arena phases are numbered by the order they appear in the fight, rather than
corresponding exactly to fight phases (since arenas are reused in different phases)

### TOP
Arena radius: 20m

The arena is very dull in these exports because most of the colour comes from
effects, which are not rendered here

These arenas were exported before people reached phase 2, so phase names are
verbatim from the game files, and might not match up to actual phase order in-game.  
Especially odd is the phase 2 export being just an outside ring - presumably
it's not actually a real phase and just numbered so for developer convenience

All arenas were exported with ZoneFbx, as Godbert would error out when trying to
export

### T4
Arena radius: 25m

This arena is a fair bit larger than other areans, and also contains transparent
bits that just lead to the skybox ingame

Try overlaying it with a partially transparent version of another arena to see
how the sizes compare

### T8
Arena size: 43×43m
Arena coordinates: (-2.695, -105.33, -507)

Towers are inactive (under the floor) for these images

Trivia: The arena is located at quite unusual coordinates. Usually they're at
nice round integers

Diametres:
 - (Pre-) Ballistic Missile knockback circle: 16m
 - Max melee: 13m

## How to reproduce
### Exporting from the game and importing into Blender
There's two tools I use to export the zones from the game:
[Godbert](https://github.com/xivapi/SaintCoinach) or
[ZoneFbx](https://github.com/lmcintyre/ZoneFbx).
ZoneFbx tends to be more accurate (Godbert sometimes misses textures), but
sometimes it's the other way around, so I recommend using both tools and
comparing results

#### Godbert
1. Find the zone in the 3D > Territories tab and export the zone
2. Import the various *.obj files into Blender, corresponding to which objects
   you want to render (trial and error to find which ones)

#### ZoneFbx
1. Find the zone path in TerritoryType.exd via Godbert or similar (should look
   something like `ffxiv/roc_r1/fld/r1fz/level/r1fz`)
2. Export the zone from the game with the found path
3. Import the zone .fbx file into Blender with scale = 100
4. Hide any objects you don't want to render, such as unwanted phases. (Tip:
   Shift+click on the eye and camera in the scene collection to hide all children)

### Rendering in Blender
1. Manually delete any unwanted objects (usually for special mechanics) that
   obscure the arena
2. Set camera position XYZ to be centred on top of the arena
3. Set camera rotation 0° on all 3 Euler angles
4. Set camera lens type to "Orthographic", with scale = 60
5. Adjust camera clipping appropriately for the scene
6. Set render engine to "Workbench", lighting to "Flat", colour to "Texture", film to "Transparent"
7. Set output resolution to 3000×3000 px
8. Render and save

The exported model often contains lots of "duplicated" vertices, that make
selecting entire objects difficult. Fortunately, Blender can automatically merge
overlapping vertices together:

1. Select the entire scene in edit mode
2. Mesh → Merge → By Distance
3. See "Removed xxxxxx vertice(s)" message appear in the info log
4. Now "Select → Select Linked → Linked" works better for selecting entire objects
