CE Editor - The complete guide

1. Installation

1.1. What do you need ?

    DayZ installed on your computer
    DayZ Tools installed on your computer

1.2. How to install DayZ Tools ?

Open steam => Place your mouse cursor on "Library" to open a dropdown menu => Click on "Tools"

![aWmJzsW](https://github.com/user-attachments/assets/16c88b3a-846b-4e4e-ae20-02638c1c301b)


Now search for "DayZ Tools" and download it

![Fx0dwdd](https://github.com/user-attachments/assets/a1193fdc-aa5f-49bc-bcea-5ff28a520314)


2. Setting up the CE Editor

Now launch the Tools by Right clicking on it and click on "Play Game..."

![jUyyqdW](https://github.com/user-attachments/assets/a475be5a-033a-41c4-af4a-c7a0f625ab33)


If a pop up ask you what steam need to launch, select "Play DayZ Tools"

![0WIHAtL](https://github.com/user-attachments/assets/ec8b6c7b-bb74-44d2-bfad-8bfcaa6ef2bc)


You should now see a software named "DayZ Tools" with a lot of buttons ! You know want to click on the "Economy Editor" button as shown on the next screenshot.

P.S. as you probably saw, you will have a some text at the bottom indicating if everything is working. Make sur you have at least the Tools as Y

![y3n1cBx](https://github.com/user-attachments/assets/1be07419-123f-4d2b-8373-ec573e314058)


2.1. ChernarusPlus and Livonia

Download this package : https://github.com/BohemiaInteractive/DayZ-Central-Economy/archive/master.zip


Now extract the zip !

You should now have a "DayZ-Central-Economy-master" folder with 2 folders and 1 file

![R0Ys2GX](https://github.com/user-attachments/assets/f30882a6-7c2f-4aab-bc71-6163b362c417)


Comeback to your DayZ CE Tool and open the file "chernarusplus.xml" located inside DayZ-Central-Economy-master > CETool > ChernarusPlus

This is going to create a complete project for Chernarusplus in 1.04 at the time I'm writting this guide.

![JLwiMVj](https://github.com/user-attachments/assets/5403e3cd-0906-44bd-91a8-12318a4032ad)


![G1OEwEm](https://github.com/user-attachments/assets/d68fd09c-4185-4cd2-b94c-2abc3c848a76)


You should now have a similar result than mine screenshot (click me if you want to see it in very big)

![r5MmfwQ](https://github.com/user-attachments/assets/e133121d-0372-4e96-92d2-45c1f1cbcc03)


Congratulation ! You have a working project ! You can now skip to the part 3 "Using the CE Editor" 🙂

2.2. From scratch (for map makers and advenced users)

This guide from @Matthew Longtime should explain you the basics of how to do it. I sadly don't have time to complete this part of the guide.
https://www.youtube.com/watch?v=7dMnuKkA49U

2.2.1. Map

2.2.2. AI spawnpoints (infected, animals)

2.2.3. Loot spawnpoints and Tiers Zones

3. Using the CE Editor

3.1. The Controls

CTRL + Mousewheel => Zoom and Dezoom on the map at your cursor

SHIFT + Mousewheel => Navigate Verticaly

ALT + Mousewheel => Navigate Horizontaly

CTRL + S => Save your project

CTRL + SHIFT + S => Save also your project and export all the data (long process)

Shift + S => Switch to "Select/move territory zones" mode

Shift + A => Switch to "Place new zones into territory" mode

Shift + D => Delete the selected territory zone

 

All checkbox allow you to see permanently (until you turn it off) the information of this checkbow (tier zone, zombies spawn points, fresh water location, etc).

If you want to turn of all the layers click on "hide all" located on the top left of the software

![Tqc2SHh](https://github.com/user-attachments/assets/65c5cb3e-87c7-43c9-b60e-823f3701e000)


If you don't see the Left or Right window of the tool (or even the map) open the "View" tab on the top left corner to active the missing(s) window(s).

![dbT3MkF](https://github.com/user-attachments/assets/31af10d1-61b6-43d2-a17a-a9da30e39561)


3.2. AI spawnpoints  (infected, animals)

The right of the software should have two windows "Territory Types" and "Properties". If it's not the case it means it's gone somewhere it shouldn't... Good luck ! 🙂 

![VZxQtiW](https://github.com/user-attachments/assets/e5c6e222-4edd-4fd8-8ff3-184dfc6b7d43)


3.2.1. Infecteds

In the Territory Types window you should see a item named "zombie_territories" with a closed dropdown. Open it !

![rdhMWZj](https://github.com/user-attachments/assets/b6dac449-7ad3-47be-8ca4-834c42e15947)


Here we have all the types of categorise of zombies like Army, Medic or Police for example.

Let's say I want to add some military and religious zombies at the main airfield of the map !

I'm going to select the "Army" tab and click on the big green Plus

![u0dPNik](https://github.com/user-attachments/assets/dced7cb1-0013-4114-8244-4c2133e7b147)


You should also start to see some new stuff on the map with a green color and a zombie logo in the middle of thoses circles. This is where Military zombies are going to spawn !

![v4qynSb](https://github.com/user-attachments/assets/74b648ce-4408-42e5-85f5-cb00c18a8baa)


Because I have choosen to click on the "Plus" button, I am going to add a new zombie spawnpoint instead of modifying one explainning why a new circle just popped on the second screen

![jK3z728](https://github.com/user-attachments/assets/91bffddb-b161-42f6-a6a3-d019f3ed28b4)


Howerver as you can see we have not a zombie icon inside this new green circle... What we want to do is to select the "Hand" button which is next to the "Plus" button as shown

![UOY4Q4p](https://github.com/user-attachments/assets/7c835e70-3da0-4b67-9d86-03b5ddab59ce)


And select your new zone

![ViklgPI](https://github.com/user-attachments/assets/dfc4f2c6-0689-46c8-8b15-70eb9f83a02e)


As you can see a red dotted square is showing us what zone we have selected while the "Properties windows is not anymore locked !

    Color and opacity is only here to help you to visualise better
    The total of entity on the map
    Because I have selected the "Army" tab this is the total number of military infected on the map
    Help you to decide if a zone should be in front of any other clipping zone or behind
    The radius of the zone, the minimum you can set is 50
    The static is the min and max of infected who should spawn even if not a single player is around (THIS INFORMATION NEED TO BE VERIFIED)
    The dynamic is the minimum and maximum number of infected that can spawn if a player is nearby
    What the zone is ? Mostly used for animals, the names speaks by themself.
    But for the zombies we are only going to use the "Dynamic Event"
    Now that you have selected the "Dynamic event" the icon changed to a zombie and you can now write into the little input box.
    This is where we are going to tell the game what type of infected are really going to spawn ! (yes even if we are inside the "Army" tab we have to tell what type of zombies are going to spawn). the file events.xml from your mission (e.g. dayzoffline.chernarusplus/db/events.xml) will contain all the categories of Infected you can use and spawn. Here is a list of the most common categories you will find:



Village => InfectedVillage

Army => InfectedArmy

Firefighter => InfectedFirefighter

Industrial => InfectedIndustrial

Sollitude => InfectedSolitude

City => InfectedCity

Medic => InfectedMedic

Prisonner => InfectedPrisoner

Religious => InfectedReligious

Police => InfectedPolice


We want to spawn military zombies so we are going to write "InfectedArmy" inside the input box and we going to set a minimum and maximum number of zombies for this zone with a custom radius as shown in the next picture

![3jZVUsa](https://github.com/user-attachments/assets/707c6bc3-6153-4cc0-9607-561afcd91c6c)


![h3PYpXp](https://github.com/user-attachments/assets/c176299a-93a2-4296-8ca0-f73d52649f16)


Now we can repeat the process to add a new Religious group but you are maybe going to get a result similar to mine

![JQeKLvv](https://github.com/user-attachments/assets/95fe3a6c-e2bf-45e3-9b56-7125e51d48f7)


How can I see the military zones while playing with the religious zones ? Just by doing that ! (see image bellow)

![IzTeVzs](https://github.com/user-attachments/assets/f79b453e-e6ff-483a-b4c3-a35e3a7076cd)


3.2.2. Animals

This time, instead of having one tab for one "type" of zombie we have one tab per group. The idea is to keep the group of animals where we want because we don't want our wolves to go for no reason outside the map or to travel the entire map just to go drink some water...

We are going to do a right click on "wolf_territories" and "Add Terriroty" to create our new group of wolves !

![tINdImJ](https://github.com/user-attachments/assets/8d39f80b-10da-4572-9893-958039f4ca7c)


Now a new "Territory" should have been created at the bottom of the list with a black opaque color by default

![jfhXCBo](https://github.com/user-attachments/assets/2203aa08-d313-424a-a7ec-979c096720ad)


You can change the opacity and the color if you want to follow the color code used for the other "territories". Oh and you can also rename your new ''territoryxxx" by right clicking on it !

We are now going to add some "zones" by choosing the "plus" button and click on the map where we want to. In my case I am going to place my zones nearby Blake lake (East of Krasnovtav and North of Berezino)

![CmmIwRz](https://github.com/user-attachments/assets/5ce670c7-5c51-45ae-8b38-d1eb37c6edf7)


If we inspect the properties of this zone we can see the zone is set by default to "HuntingGround" meanning is going to hunt for animals and survivors in this area.

![ziVTyHP](https://github.com/user-attachments/assets/02ae204d-7cc8-4daa-a143-4d6af13fe04a)



Rest => Where the group of animals are going to rest

Graze => Where the group of HERBIVORE animals are going to eat

Water => Where the group of animals are going to drink water

HuntingGround => Where the group of CARNIVORE animals are going to hunt


All you have to do is to create more zones and change the "AI Usage" to diversify their behavior. You don't have to touch to the Static and Dynamic values with the animals.

![Ae3fEW9](https://github.com/user-attachments/assets/2a8e2166-29bd-40e9-8619-2d12f06bf71d)


Now you have probably understood how to create and modify a "territory" but in case you still don't know how to modify a existing "territory" all you have to do is to select it and use the "cursor" button to select a "zone" and tweak the values !

3.3. Loot spawnpoints and Tiers zones

In this guide I am assuming you know how the loot is spread on the map. This topic need a seperate guide on itself so I wont explain it here.....

But let's explain what all those colors means on your screen !

![PazCxSP](https://github.com/user-attachments/assets/500cf70b-77f5-4be5-abe9-ec8f8d7093c5)

water-fresh => Where the water is clean "fresh"

keyPoint-Churches => Where the Churches are located on the map

valueFlg_Tier1 => The Tier 1 area

valueFlg_Tier2 => The Tier 2 area

valueFlg_Tier3 => The Tier 3 area

valueFlg_Tier4 => The Tier 4 area

ushFlg_Def-All => All the loots location from all the types of locations

ushFlg_Def-Coast => All the loot spawns related to boats

ushFlg_Def-Farm => All the loot spawns of farms, barns, small shacks

ushFlg_Def-Firefighter => Do I really need to explain you all of them ? 


As you see on the picture bellow we can see all the military loot location if we have selected the "ushFlg_Def-Military"

![5PORBIB](https://github.com/user-attachments/assets/86743e1f-4f83-400c-9e30-69b8cace3576)


If I want to set the Prison Island as a Firefigher loot area for one or two building this is what I need to do :

Select the "ushFlg_Def-Firefighter" and zoom to the prison island, you should just see the map of the island and some water around it.

Just under the map on the bottom left corner you should be able to see a checkbox names "Paint mode" as shown in the picture

![qbV0Rpc](https://github.com/user-attachments/assets/8b571b18-c623-4bd3-a9f5-6ac5becec94a)


When activated you are probably going to loose the bottom part of your software. And here we have a issue, the Properties of the "territories" is overlapping the "Brush" window !

My personnal solution is to take the "Properties" window and move it somewhere else the time to do my manipulation. If you prefer to keep the "Properties" window at the original place you can also take the "Brush" window and do the same.

Now you maybe want to get your bottom part back, just press twice this icon on the top right corner. u86yUBd.png

Now you should have everything back and you have now a yellow cursor while navigating on the map !

Before painting everywhere let's see what the "Brush" window as to offer

![NhnU9Ki](https://github.com/user-attachments/assets/e86fad75-1f6d-4df4-ada8-37747468903e)


    Size is for the size of your cursor for painting/erasing
    Color and opacity is just for you to help you to see better what you are doing, nothing else
    Outline is exactly what you are thinking about

I have painted where I wanter my loot to be categorized as firefighter loot as you can see

![RlWj1Ce](https://github.com/user-attachments/assets/6a36f48a-056d-48cf-8416-36c3f0af2d82)


It's as simple, just try to make it cleaner than my example if you don't want any surprise😅

4. Saving your work

You can use press CTRL + S to save or CTRL + SHIFT + S to save and export all the data  (long process)

Or you can also go here

![jBuf7IA](https://github.com/user-attachments/assets/57f1c1c3-0055-4255-a0cf-b2854b84091d)


4.1. AI config

If you want to save only your Territory Types config files (zombies/animals spawn points) you can use the following options :

    CTRL + SHIFT + S => going to save and export everything (long process)
    Export Selected => Export the selected territory (in this case the "zombie_territories")
    Export All => just as you expect, export all the Territories as once

![0g5ocfm](https://github.com/user-attachments/assets/2dd148c4-acf4-4be3-ae4c-c5835c898e70)

You should now have a new folder inside your project nammed "territoryTypes" with the config(s) file(s) you have exported

![YFb4Ui9](https://github.com/user-attachments/assets/016e7abe-00bb-441a-a55f-06d8e1b86f8c)


4.2. Loot economy config

The only option I know is to do the "CTRL + SHIFT + S", this is going to take some times and will create a new folder for you with a big file named "chernarusplus.map" or "yourprojectname.map" inside the map folder as shown on the screen.

![50AIrvW](https://github.com/user-attachments/assets/a95f3c15-a897-4c3a-a80e-a3d4c99de1ed)


5. Playing with your custom config

All you have to do is to take your territoryTypes files and drag them inside the "env" folder of your mission to replace them (you can also do a backup in case)

![XMc2JtJ](https://github.com/user-attachments/assets/7e5a8f14-36f6-4b8a-8109-2d31491b6ed9)


If you want to use your custom loot location config, you need to go the folder "map" and also drag and drop the "chernarusplus.map" (or the name your projecthave.map) inside your mission and not inside db, env or storage_something !

After that, you just need to rename yout "chernarusplus.map" to "areaflags.map" (you probably need to rename or delete the old file using this name before doing that).
