# GDIM 33 In-Class Activities
## W1
### Activity 1
Mood board
https://docs.google.com/drawings/d/1hSHmBo_q8wHiGlY9Ql2y9L7SmEXqM5fOtnJkqHCPkcs/edit?usp=sharing

1. What patterns are emerging from your inspiration sources- are there any particular gameplay mechanics, genres, 
or non-game-related aesthetics you’re consistently interested in?\
Genres: anime, nature, perhaps horror?
Gameplay mechanics: exploration, building, surprise jumpscares

2. Chat with at least one of your table mates about what they’re interested in building. How are your personal styles and interests similar?\
Zom shares a love for singleplayer exploration-oriented games like Death Stranding, as well as anime/cel-shaded aesthetics on occasion. 

3. Chat with your table's LA about their taste in games. How are their tastes similar to yours?\
I talked with Agnes, who has an interest in RPG action-oriented games. She mentioned Baldur's Gate 3, which has both RPG elements and a big focus on exploration. In my mood board I included a few RPG games, notably Honkai: Star Rail and Genshin. 

### Activity 2
Genre:\
Horror, with cel-shaded aesthetics.\
Core mechanics and gameplay loop:\
Explore the environment. This is a loop. Essentially there will be ‘rounds’ where you have to survive against a robot. You enter a room, have a certain amount of time to prepare, before a robot is unleashed on you. Materials are randomized–while the layout of the environment will be the same, the materials found in the environment are randomized. You consume resources to preserve sanity and can attack the robot to temporarily disable it. You have to survive for a certain amount of time before the round is over. Survive for 10 rounds to win. Each round gets progressively harder (less resources and faster robot movement/detection).

https://docs.google.com/drawings/d/1GYoHn-SyWO8b-bVhteKCuFZDn7f3TTmgD896zbSOpeE/edit

## W2
No devlog

## W3
Activity 1:
https://docs.google.com/drawings/d/1GYoHn-SyWO8b-bVhteKCuFZDn7f3TTmgD896zbSOpeE/edit
Same link but it has the updated breakdown.

Activity 2:
Why is it advantageous to save the event name for the explore-to-dialogue state transitions as Scene variable ("clickNpcEventName")?
This way, if you have multiple game objects that need to trigger the dialogue state, you can easily access it in their respective graphs.

Describe how using at least one Debug.Log() node helped you test your Graphs at an intermediate step.
I had trouble with disabling the animals from falling; when I added the Debug.Log() node after the For Each loop to see what happened, 
the For Each loop wasn't run at all. So I went back to that node to see what was wrong, and figured out that I wasn't properly calling the contents of the list. I had
the list plugged into its input node, but never actually called the contents of the loop for each script machine in the list. I was actually just calling it on the game controller,
which doesn't have a script machine attached to it nor should it even be disabled. Ultimately, I just had to plug the items output node into the Set Enabled node to make it trigger for each element in the list.

Is the Set Cursor Lock State relevant to your Vertical Slice? Why or why not?
Yes. The player will be controlling the direction that their character travels in by their cursor, which means that it'll have to be unlocked anytime they access their inventory or pause/menu screens,
and locked whenever they're actively moving in game.

Is the concept of a "game state" relevant to your Vertical Slice? Why or why not?
Yes. For my game, there are 3 primary game states. Menu/lobby, exploratory state, and unleashed state. The first is self explanatory. The exploratory state is when the player is exploring the hotel
for resources, and the unleashed state is when the robot has been unleashed and the player is running from them.

## W4
Activity 1:\
Currrent playable state:\
Movement across a flat plane and robot AI (has 2 completed states - can wander around, and can chase the player depending on proximity)

Goals:\
1. Find if players like the movement system
2. Find out players’ opinions on enemy (yellow ball)

---------
Playtesting people:\
Zoya
Andy
Julie
Isabel
Kristin

Playtesting feedback:\
1. using the left control button as the sprint button causes the tab to close, since ctrl+w close your current tab. I did not know about this before.
1. using shift to sneak and control to sprint may be odd/unusual, as many games have the shift key as their sprint button.
2. confusion on what the enemy does

Activity 2:\
Assuming this activity is completed by a programmer, could a writer add more dialogue to this setup without writing any code? Why or why not?\
Yes. They can add dialogue by creating more DialogueLine scriptableObjects. It doesn't require the writer to write code, but rather fill in the 'line' and the resulting reply node. 
Everything else is managed by the scriptableObject.\


What limit is there to the number of dialogue nodes that the writer could create without writing any code?\
4, since that's how many buttons fit on screen at once. But in terms of reply chains, it could go on for as long as the writer needs it to be.

In your own words, describe the purpose of the "Regenerate Nodes" button.\
It refreshes the nodes that you can use in graphs by looking through your project files and seeing if there's anything that can be turned into a node (anything that has the characteristics in the form of methods and classes).

## W5
Activity 1:
Goal: item spawning system
Features:
-randomly chosen spawn coordinates
	-call on C# code to get spawn locations
-randomly chosen item
	-call on C# code to get items
-resets at the beginning of each new round
	-removes all instantiated items (refer to W4 in class activity for nodes used) inside of visual scripting. 

Step 1: Create spawning locations on the map
	-These will be empty gameObjects, whose only purpose is to hold the location where an item could appear at.
Step 2: Create C# script with list of spawnable items, and a list of spawn locations
	-Script will take random spawn locations, obtained by creating a SerializeField for a list of spawn locations. 
	It should also take the list of possible items to spawn in; also obtained the same way. Can test via 2 debug logs printing out all items in the lists.
	-Script will then check whether the location already has an object in it. Whenever the script selects a spawn location, 
	remove that spawn location gameObject from the list. Can test using a debug log that prints out the remaining items in the list.
	-Script will then select a random spawn location using random(). It also selects a random item to spawn at that location. Can 
	test via a debug log printing out the spawn location gameObject’s name, and a debug log printing out the item that would be spawned there.
	-Has a method that creates a node that will call the C# code. testable via being able to get the node in any visual scripting graph. 
	Regenerate nodes after creating said method.
Step 3: Connect C# script to the GameController state machine and ensure it works as intended
	-Getting the items to spawn in: connect necessary nodes to access the C# code in the GameController state machine; 
	specifically inside the LevelLoader state. If successful, when the game is run, items should spawn at the predetermined locations.
	-Getting the items to despawn: connect a For Each loop that deletes all items in the spawnedItems parent GameObject, 
	similar to the W4 in-class activity. If successful, when the game is run and the round is over, the items are despawned from the environment.
	-Getting the items to despawn part 2–player inventory: do the same things as the previous step, but for the player inventory. 
	This way, any items the player has in their inventory will be deleted. If successful, when the game is run and the round is over, the items are removed from the player.

Activity 2:
Completed step 1 and 2, but didn't fully complete step 3 (still need to implement despawning for player inventory)

## W6
Activity 1:\
Currrent playable state:\
New features include...
1. Items!
2. Item spawning system (random spawn location and random items)
3. Player inventory (UI is not finished yet)
Also adjusted player speed.

Link:
https://asphalt-asurada.itch.io/hylan-hotel-milestone-2

Goals:\
1. Find if players like using the items
2. Opinions on the item spawning system

Noah: likes the item system, but there should be an indicator that tells you when you can pick up an item
Kristin: likes the items, but wishes the monster would be bigger or easier to see
Andy: likes the items, but did not know what the win or loss condition was.
For all 3, controls were not intuitive besides for the WASD keys.

Activity 2:\

1.Why does the Multiply setting of the Blend node make the resulting color darker and less saturated than the input colors? 
Hint 1: The Multiply option literally multiplies the values given, so a vector A = (R1, G1, B1) Blended with a vector B = (R2, G2, B2) with the Multiply option will result in a vector C = (R1*R2, G1*G2, B1*B2).
Hint 2: recall that we store the RGB channels as 0.0 - 1.0 values.
Since a value closer to 0 results in a darker/less saturated color, multiplying all channels results in a darker value because the resulting number is lower than the two original numbers. 

2. If we use Multiply to combine Alpha values, will the resulting value be more or less translucent than either of the original values, and why?
It becomes more transparent as the resulting value gets closer to 0.

3. When we created the SampleTexture2D node, Unity auto-created the UV0 Node for us to get the UV coordinates for sampling the texture. 
Where does the shader get these UV values from?
It gets it from the texture.

4. You just learned that you can manipulate colors with math. Does that sound interesting or exciting to you?
Pretty interesting because it's similar to Blender's material editing process.

## W7
1. For our vertex color shader in step (3), where did the data for the Vertex Color node come from?

The vertices on the shiba model.

2. Since vertex color is stored as data in each vertex of the mesh, why is the color on our shiba from step (3) blended at the edges of different regions of color?

It is approximating, based on the data from each vertex that makes up a face, what colors should be between the vertices.

3. Why is the shiba from step (3), which is colored with vertex color, less detailed than the shiba we rendered with a texture in last week’s activity? 
Given that vertex color generally results in a less detailed color application than applying a texture, what can you imagine vertex color is useful for?

The color info stored in each vertex can only be used to approximate the colors in between, which is not as detailed as having a UV map that has the exact color mappings between each vertex. 
It'd probably be more useful for low detail/low poly models, or quickly testing colors for a model.

4. Based on the color of the shiba in step (4), does anything look wrong with the mesh’s vertex normals?

There are some locations on the mesh that have a sharp change in color. For example, there is a big change in color on the model's back left leg, where 2 vertices' normals seem to be rotated the wrong way.

5. We used the color output of a shader to visualize a mesh’s vertex normal values in step (4). 
Name one other piece of vertex data (or any kind of data) you can imagine testing with a debug shader like this, and describe why that might be useful.

Since we animated something using UVs, it might be helpful to check the associated position that a vertex has to a UV map. If you had a wave animation, you could use it to
check whether the model would have smooth lighting.

6. Why is there an error in the lighting in step (5) on the back of the Shiba?

Its normals on those two vertices are angled incorrectly.

7. Why do you think we set the Blend Mode to Additive for the fire effect in Step (6)?

It keeps the darkened sections of the fire effect transparent because the Blend Mode changes how colors are calculated with the material of the fire effect itself and the colors behind it.
Since there is an alpha channel, it needs to account for everything behind the fire effect. Multiply would have taken the color of the materials behind the fire effect, and multiplied it by
fire effect. So the whole effect gets darker because multiplied color values have a value that's lower than the original two. However, additive only adds the values. So if something is transparent 
(has an alpha value of 1), adding a color behind it (probably a value of less than 1) doesn't change anything, and allows it to remain transparent.

## W8
### Activity 1
What is new:
Polished bat functionality, and updated main menu cutscenes.

[Link](https://asphalt-asurada.itch.io/hylan-hotel-milestone-3) to new build

Playtesting Goals:
-Find out if players can play the entire game without any assistance.
-Find out if players are going out of bounds or struggling (dying quickly to the robot)
-Whether any in-game feedback is confusing.

Playtesters and their feedback:
Noah:
-Had no trouble playing through the rest of the levels once he understood the controls. 
-Died the first round. Why? "It's hard to tell when the enemy is on you or not." However, once he understood the objective, it was quite easy to win all levels.
-Went out of bounds at level 5
General feedback:
	-not a ton of player feedback
	-dont know when they are hit by the robot
	-no solid goal other than to sit in the corner of the map
	-speed effect understood
	-bat mechanic not understood. Couldn't tell what the bat would be used for.

Julie:
-Did not know how to use items
-UI could be clearer to know when you are holding an item in your inventory
-Clipped out of bounds several times when near the stairs

### Activity 2C
1. Open the Frame Debugger window under Windows >Analysis > Frame Debugger. What's the name of the pass associated with the post-processing effect we created? 
Other than the name being kinda obvious, how can you tell?

FullScreenPassRendererFeature. We can also tell by checking what shader is being used in the draw call. The pass has a draw call that is using the TestPostEffect shader.

2. What does the screen look like if the Lerp value is set to 0.5? What about 0? What about 1?

0.5: equally blended between the cobblestone texture and the regular scene.
0: cobblestone texture cannot be seen at all.
1: cobblestone texture covers the entire scene, and only the tomatoCat can be seen.

3. WHY does the screen look like that based on those different Lerp values?

The lerp value determines how much the cobblestone texture should be shown. It's kind of like the alpha channel, where 0 is fully transparent and 1 is fully opaque.

4. Why does our algorithm for the Lerp amount use (sin(time)+1)/2 instead of just sin(time)?

The sin curve oscillates between -1 and 1, which we don't want half of (anything less than 0 just means the entire effect disappears, and the screen gets brighter). To fix this, we need
to add time+1 and then divide by 2, so that it oscillates only between 0 and 1.

## W9


## W10