If Quake 2 Was 2D
=================

I share this code in hope it will help someone learn a thing or two, even if it's how NOT to write C++ code :P
I have made a lot of mistakes working on this project and I have learned a lot. This project is not a representation of how I structure my code today, and code-wise it has nothing to do with my Broken Mug engine project.

This project is based on a heavily modified engine from the book Advanced 2D Game Development (2008) by J.S. Harbour:
http://www.amazon.com/Advanced-Game-Development-Jonathan-Harbour/dp/1598633422

It's written in C++, uses DirectX for input and rendering, and FMOD for sound. You can find more info about this project on my blog:
http://antonior-software.blogspot.com/p/if-quake-2-was-2d.html

Gameplay video (click to watch):  
<a href="http://www.youtube.com/watch?feature=player_embedded&v=M_Vbn4ssY-M
" target="_blank"><img src="http://img.youtube.com/vi/M_Vbn4ssY-M/0.jpg" 
alt="Gameplay video" width="576" height="360" border="10" /></a>

Screenshots:
![alt text](http://i.imgur.com/X60KY.jpg "random")

![alt text](http://i.imgur.com/U23hO.jpg "splitscreen co-op")

![alt text](http://i.imgur.com/r5e9V.jpg "map editor")

How to build ?
========

The repository includes the source code and VS 2008 projects for the engine and the game.  
The game assets can be downloaded from the link on my blog.  

You need to have DirectX SDK installed. In Visual Studio the include and library directories need to be set:  
VS 2008->tools->options->projects and solutions->vc++ directories:  
Include files:  
C:\Program Files (x86)\Microsoft DirectX SDK (June 2010)\Include  
Library files:  
C:\Program Files (x86)\Microsoft DirectX SDK (June 2010)\Lib\x86  

Open the projects and create solutions for both projects in the same folder as the project file.  
Then you need to build the engine as a static library. Be sure you set to build as "release". The engine.lib file should be located in the Release folder.  

Then link the game project to engine and other libs and build as "release". The game.exe file should be in the Exe folder.
Put the game assets there and run Game.exe file.  

Game project dependencies:  
VS 2008->project->properties->configuration properties->linker->input->aditional dependencies:  
"..\Engine\Release\Engine.lib"  
"..\Engine\fmodex_vc.lib"  
d3d9.lib  
d3dx9.lib  
dxguid.lib  
winmm.lib  
dinput8.lib  
user32.lib  
gdi32.lib  

Issues
======

I can't say I'm proud with my code, but it works and the game itself is not bad at all, if I dare to say.  
When building the projects there will be hundreds of warnings, because I didn't bother cleaning up the code.  

Bugs
----
- Collision code is a disaster, but it works in most cases. On high framerates (>150 FPS) there are collision problems on the edges of the sprites and when player goes from one platform to another(player animations switch rapidly).  
- Explosions don't seem to work in co-op when the players are in different maps  

Updates v1.0.1
-------------

- Animations no longer speed up on framerates higher than 1000FPS (GetDeltaFix())  
- Biomech rocket does damage to the player  
- Added frame lock in options menu (that doesn't really work, turn on vsync instead)  

