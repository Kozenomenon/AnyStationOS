![AnyStationOS](ASOS_Repo_Icon.png)
# AnyStationOS
 Ark Mod that demonstrates how to add your engrams to any craft stations by editing the PGD Additional Structure Engrams array at runtime.
 
## Setup
Copy the *AnyStationOS* folder to your kit's \Mods directory.
Start the Ark Dev Kit. That's it. 

The *AnyStationOS_CCA* asset is the singleton that does all of the work. This is what you will want to be looking at.

The \Examples folder has the Mini Oil Pump I put in just to show how the engrams can be added to existing structures.

I have put a lot of comments in the graphing of the singleton so I hope it for the most part does need much further explaining here.

## Notes
* The singleton is a child of *SaveGameActor* only so that it will load earlier on restarts. I found that by doing this the mod did not need to perform checks on existing structures anymore.
* There is logic included for checking existing structures, but it will be disabled by default. It can be enabled via INI (below).

## INI Settings
```ini
[AnyStationOS]
DebugMode=True
MiniOilPumpMatches=*Fabricator*,*Smithy*,*Replicator*
DoExistingStructuresCheck=False
DoClientPGDEdits=False
```
**DebugMode** 
Enables logging via PrintServerGameLog.
**MiniOilPumpMatches** 
Comma-delimited list of match strings for which structures to add the Mini Oil Pump engram to.
**DoExistingStructuresCheck** 
If True will perform check on server for existing structures missing any of the added engrams. If missing, the engram will be added to the structure. I left this in here in case anyone finds that they need it. Once I made the singleton a SaveGameActor I found that after the first game/server start the logic ran early enough and this was not needed. So I made this disabled by default.
**DoClientPGDEdits** 
If True the singleton will set itself to be replicated and it will run the PGD array merge on clients as well. I found that this was not needed, but left it in here disabled by default just in case.
