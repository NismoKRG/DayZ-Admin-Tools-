DayZ-Admin-Tools
================
this project includes code that i did not wright but have permission to use
https://github.com/nomadichayward/DayZ_Dual_Admin_Debug_Monitor

Install Instructions (chernarus)
=====================
make these changes to your init.sqf

under "filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";
add this

playerstats = compile preprocessFileLineNumbers "debug\playerstats.sqf";

at the bottom of init.sqf add

[] execVM "admintools\Activate.sqf";

find this code 

if (!isDedicated) then { // If mission is loaded by a player execute the player monitor
0 fadeSound 0;
0 cutText [(localize "STR_AUTHENTICATING"), "BLACK FADED", 60];
_id = player addEventHandler ["Respawn", {_id = [] spawn player_death;}];

and change the playermonitor line to
_playerMonitor = [] execFSM "admintools\player_monitor.fsm";


in admintools\AdminToolsMain.sqf, and debug\playerstats.sqf
locate this code

 if ((getPlayerUID player) in ["#######","#######"]) then {
 
change ###### to your admins player id's

Profile>>"PlayerName">>Edit, look in the bottom left hand corner for "Player ID" 
that is the number that needs to be added to the code 

in debug\playerstats.sqf

locate this code and change "Server name here" to what ever you want

// <t size='1.15' font='Bitstream' color='#5882FA'>Server name here</t><br/>", \\

once you have all of this done pack and replace your mission.pbo

if your player ID has been added to the correct portions of code a option will be added to the scroll menu

Install Instructions (Taviana)
=====================

find this code in init.sqf

"filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";

add this code under it

playerstats = compile preprocessFileLineNumbers "debug\playerstats.sqf";

find this code in init.sqf

if (!isDedicated) then {
	0 fadeSound 0;
	0 cutText [(localize "STR_AUTHENTICATING"), "BLACK FADED",60];
	_id = player addEventHandler ["Respawn", {_id = [] spawn player_death;}];
	
	and change the player monitor line to this
	
	_playerMonitor = [] execFSM "admintools\player_monitor.fsm";
	
	at the bottom of init.sqf add this line
	
	[] execVM "admintools\Activate.sqf";
	
	locate this code in debug\playerstats.sqf, and admintools\admintoolsmain.sqf
	
	if ((getPlayerUID player) in ["########","########"]) then {
	
	change ###### to your admins player id's
	
	in debug\playerstats.sqf
locate this code and change "Server name here" to what ever you want
<t size='1.15' font='Bitstream' color='#5882FA'>Server name here</t><br/>",


once you have all of this done pack and replace your mission.pbo
if your player ID has been added to the correct portions of code a option will be added to the scroll menu
battleye
=========
theres are all of the changes that need to be made
do NOT delete the line only add the exception if you need a exzample please go here
http://opendayz.net/threads/dayz-admin-tools.8576/page-34#post-33299
These are all the changes I made in my scripts.txt
Code:
----------------------------------------
script restriction !exception
----------------------------------------
//dayzesp.sqf is the only one I went line by line and made all the exact restrictions for
5 addGroupIcon !"dayzesp.sqf"
5 setMarkerPosLocal !"dayzesp.sqf"
5 onMapSingleClick !"dayzesp.sqf"
5 setPosASL2 !"dayzesp.sqf"
5 openMap !"dayzesp.sqf"
5 drawIcon !"dayzesp.sqf"

----------------------------------------

1 addPublicVariableEventHandler !"healp.sqf"
5 setHit !"healp.sqf"
1 setVariable !"healp.sqf"

-----------------------------------------

5 setVehicleAmmo !"looknrepair.sqf"
5 setDamage !"looknrepair.sqf"
5 setDammage !"looknrepair.sqf"

------------------------------------------

5 "zombieshield" !"zombieshield.sqf"

------------------------------------------

//covers all the weapon switches/backpack changes
5 addWeapon !"items.sqf"
5 addWeaponCargo !"items.sqf"
5 addMagazine !"items.sqf"
5 addMagazineCargo !"items.sqf"
5 addBackpack !"items.sqf"
5 addBackpackCargo !"items.sqf"

--------------------------------------------

1 allowDamage !"Godmode.sqf"
1 allowDammage !"Godmode.sqf"
5 setDammage !"Godmode.sqf"
5 setVehicleAmmo !"Godmode.sqf"
5 "God mode" !"Godmode.sqf"
5 GodMode !"Godmode.sqf"

---------------------------------------------

5 setDammage !"cargod.sqf"
1 setFuel !"cargod.sqf"
5 setVehicleAmmo !"cargod.sqf"
5 "God mode" !"cargod.sqf"
5 GodMode !"cargod.sqf"

---------------------------------------------

Example for some of the lines...

Script Restriction | Exception

5 setMarkerPosLocal !"\"setMarkerPosLocal\"," !"dayzesp.sqf"," !"rsetMarkerPosLocal = 'setMarkerPosLocal'" !"rsetMarkerPosLocalcode = compile PreprocessFile (BIS_PathMPscriptCommands + 'setMarkerPosLocal.sqf')"


5 setDammage !"\"setDammage\"," !"looknrepair.sqf"," !"Godmode.sqf"," !"cargod.sqf"

I like to put my exceptions near the beginning rather then the end since I find it easier to find them if I need to later on.


FAQ
====


Q: I teleported and now i cant move

A: press w + space


Q: how do i return to my body after spectating a player

A: press F3.


Q: I executed "script name" and now im stuck, frozen, glitched..ect

A: change skin to survivor, if that does not work relog


Q: I want to modify my debug monitor can you help?

A: no, post here http://opendayz.net/index.php?threads/dayz-duel-admin-debug-monitor.8402/ for help


Q: can you add "script name" to the tools?

A: possibly.

Q: i followed the readme to the letter but its not working

A: did you set your instance ID # in init.sqf