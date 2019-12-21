# WorldQuestTrackerAutoNav
Automatically navigates once you click on a world quest

# How to use

![howto](https://i.imgur.com/2HGKMd9.png)

Simply click any world quest, and you will navigate to the quest.

# Caveats

Does not currently navigate to the correct Z-Axis. Blizzard does not provide Z axis in the LUA API, so a new solution is needed. 
Currently the project uses the following functions to get the quest location:

```
-- get the x,y map coordinates of the quest
local x, y = C_TaskQuest.GetQuestLocation (questID, mapID)
-- get the 3d world x,y coordinates of the quest (z-axis missing!)
-- coords = {x: float, y: float}
local _, coords = C_Map.GetWorldPosFromMapPos(mapID, CreateVector2D(x, y))
```

# Hook Information

The changes are made the following function:

`WorldQuestTracker.AddQuestTomTom (questID, mapID, noRemove)`

As a result, the addon `TomTom` will be required for this function to fire. 
However, `WorldQuestTracker.AddQuestToTracker` would likely be suitable as well.

# Requirements

EWT (due to usage of `MoveTo`)
TomTom
