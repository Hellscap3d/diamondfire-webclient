
## eaglercraft

live demo available at https://games.nx-eags.tk/minecraft_demo/
I'm currently not hosting any servers right now if you want an ingame demo compile the modified bungeecord server and download the minecraft spigot server software 1.5.2 from https://ci.md-5.net/view/SpigotMC/

eaglercraft is a port of minecraft 1.5.2 that runs in a web browser. it uses the decompiled source of the official minecraft 1.5.2 direct from mojang decompiled by MCP (http://www.modcoderpack.com/) and therefore it is binary compatible with any minecraft 1.5.2 server through a modified version of md_5's bungeecord which proxies the browser's websocket connection to pure TCP. TeaVM is used to compile the java source to javascript, and a special compatibility layer created by your's truly allows the fixed function opengl 1.3 based rendering engine mojang uses to operate through an html5 webgl canvas with minimal changes to the source.

to compile, simply clone the repository and import the root directory as a gradle project into eclipse. run the gradle 'teavm' compile target to generate the classes.js file from the source tree. to modify the game's assets repository (javascript/assets.epk) make your changes in lwjgl-runtime/resources/ and use the eclipse project located in epkcompiler/ to regenerate the assets.epk file and copy it to the javascript directory. to run the minecraft source in desktop java mode for quick debugging using native opengl for rendering instead of webgl create a new empty eclipse project. link the src/main/java and src/lwjgl/java as source folders and add the jars in lwjgl-rundir as dependancies. Create a run configuration and add a jvm argument pointing to the lwjgl natives folder (lwjgl-rundir/natives) like this, -Djava.library.path=natives, and make sure the working directory for the run configuration is the lwjgl-rundir folder.

this project is just a proof of concept to show what can be accomplished by a skilled developer using TeaVM. it is not very fast or stable, and the only real useful portion is the emulator code which creates a makeshift fixed function opengl 1.3 context using webgl (based on opengl 3.3) operational in the browser. maybe it can be used to port other games in the future
