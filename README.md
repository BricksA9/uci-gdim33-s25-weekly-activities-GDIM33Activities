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

## W6

## W7
