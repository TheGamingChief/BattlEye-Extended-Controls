

Options:
  -h, --help   show this help message and exit
  -f FILENAME  Config file to read from
  -v           Show current Bec version and exit
  --dec        Disable external commands
  --dsc        Disable server check
  --dpl		   Disable plugins
  --enc		   Set encoding table
  
FILENAME is the name of your config file. the file MUST be located inside the Config dir..
Bec will automaticly look in the Config directory. so if you have: ..\Bec\Config\myserver.cfg
You start Bec like: Bec.exe -f myserver.cfg

Do not name your config files with space in them. Use underscore if you need to have 2 names it it, example like: foo_bar.cfg
This is a nogo. Bec.exe -f foo bar.cfg 
Do it like this. Bec.exe -f foo_bar.cfg or Bec.exe -f 'foo bar.cfg'  (using quotes with spaces) 

--dec switch will disable external scripts, this applies to both Commands.xml and Scheduler.xml
This means that no bat or cmd files may be executed.

--dsc switch will disable the wait & check for the arma server. 
Bec will try and connect directly to the rcon regardless if the server is running or not.
Note. your reporter account will be disabled if you use this option.

--dpl switch will prevent Bec from loading up plugins


--enc switch allows you to set another char table. Bec uses by default 65001. 
you can use the command chcp in a console to see current char table. 

NOTE: Bec might need admin permission to work properly. but when using the --dsc switch it should not be required.

-------------------------------------------------------------------------------------------------
Are you Upgrading from a previous version ???. 
Make sure you read the changelog.txt and check out the example files for possible changes !!!.

Do not email me for bug and such if you are to lazy reading the information given to you.
i'll ignore all emails when it's your own fault you cant get it started.

-------------------------------------------------------------------------------------------------

************** Now... What is Bec and Whats does it do!. **************
Bec , Aka Battleye Extended Controls.

Bec is Automated Rcon Tool for Battleye on Oa & Arma3 Servers.
You can consider Bec a Rcon Bot that does things automated for you.

This is a Server application only, no need for anything as a client, other than arma itself.
For Bec to work properly it depends on Battleye and a stable internet connection and ofcource the Arma server itselfeslf.

Let it also be said that this application is intended to run on the machine that also runs the server.
in other words. for optimal performance do run Bec on the same machine as where the Arma3 server is running.

What this tool does is give you the ability to:

* Give Be Power on the Chatline in-game the mission with Multi Admin Support.
* Logs Chat to file(s) with timestamps, log Be events to Own file. all organized.
* Allows you to setup multiple admins in different Groups, setup multiple custom commands with Permission levels.
* Ie. !bpl bans a player 10 min, !btk bans a player 20 min for Team kill.
* Nick filter. use file with rude, offensive names that you do not allow on your server. auto kicks player on connection.
* Setup White list file for guids, so only listed guids will be able to connect.
* Create Schedules tasks, such as modts, event notification., restart server, run external bat/cmd scripts etc.
* Create your own Python plugins.
* Bec will auto report hacks and also check players who connect against a database if you have an account.
	It requires that you signin up an reporter account, this will also give you the ability to use Bec's bansys pages.
++ more

!!! Summary !!!
* Multi Admin Support
* Define Custom Names on Commands
* Set Group Level on Admins and Commands
* Organized Chat logger
* Organized BE Event logger
* Nick Filter, Auto Kick Offensive Names Defined By You
* Word Filter. Warn/Autokick On Offensive Chat.
* Create Whitelist.
* Chat Restriction.
* Chat Spam Protection.
* Autokick Lobby Idlers.
* Create schedules.
(*) Check Guid of players who connects against a central ban database
(*) Report GameHacks To a Central Ban Database


!!! PLEASE DO READ THE HOLE FILE TO SETUP BEC ON YOUR SERVER !!!


******************************************************************************************************
!!! CONFIGURE !!!

-------------
*** Stp 1 ***
-------------

First you need to setup BEServer.cfg for BattlEye.
You need to verify that you have a BEServer.cfg. 
If its missing you need to create this file for Battleye before Bec can start to work.
In this file. create one line. like this:

Rconpassword MySecretPassWord

Save it and close.

Http://community.bistudio.com/wiki/BattlEye
Http://forums.bistudio.com for more info about that.

If you are unsure about what this file is. Do read the wiki about it. its Needed for Bec to function.

--- !!! YOU MUST HAVE BATTLEYE SETUP CORRECTLY WITH RCON BEFORE YOU CONTINUE !!! ---
--- !!! YOU MUST HAVE BATTLEYE SETUP CORRECTLY WITH RCON BEFORE YOU CONTINUE !!! ---
--- !!! YOU MUST HAVE BATTLEYE SETUP CORRECTLY WITH RCON BEFORE YOU CONTINUE !!! ---
--- !!! YOU MUST HAVE BATTLEYE SETUP CORRECTLY WITH RCON BEFORE YOU CONTINUE !!! ---


-------------
*** Stp 2 ***
-------------

Place the Bec directory anywhere you want. it doesn’t really matter where its located on your disk.
it might be anything like:
C:\Tools\Bec

Open the "C:\Tools\Config" directory and edit the files called.
* Config_EXAMPLE.cfg
* Admins_EXAMPLE.xml 
* Commands_EXAMPLE.xml
* Scheduler_EXAMPLE.xml

----------------------------------------------------------
EXAMPLE CONFIG FILE, ALL PARAMETERS DEFINED:
----------------------------------------------------------
[Bec]
Ip 			= 127.0.0.1
Port 		= 2302
BePath 		= C:\SERVER1\BattlEye
Admins 		= Admins.xml
Commands	= Commands.xml

# Optional
[Misc]
AutoLoadBans			= True
Ban						= 3
BeCustomBanFiles 		= Bans1.txt, file2.txt, file3.txt
ConsoleHeight			= 65
ConsoleWidth			= 125
AsciiNickOnly 			= True
AsciiChatOnly 			= True
IgnoreChars 			= æ,Æ,ø,Ø,å,Å
NickFilterFile 			= C:\Path\Bec\Config\BadNames.txt
WordFilterFile 			= C:\Path\Bec\Config\BadWords.txt
WhiteListFile 			= WhiteList.txt
WhiteListKickMsg 		= please connect to our ts3 for more information on howto join. ts3.domain.com
Warnings 				= 5
ServerExeName 			= myArma2_Server.exe
Timeout 				= 40
KickLobbyIdlers 		= 300
Scheduler 				= Scheduler.xml
MinPlayerNameLength		= 3
MaxPlayerNameLength		= 16
DisallowPlayerNameChars	= [](){}<>/\^¨|§!"'#¤%&@£$€
ChatChannelFiles 		= true
SlotLimit 				= 45
SlotLimitKickMsg 		= The Server has reached its player limit.


# Optional
[ChatRestriction]
Global 		= 10
Side 		= -1
Group 		= -1
Vehicle 	= -1
Command 	= -1
Commander 	= -1
Direct 		= -1

# Optional
[ChatSpam]
Lobby					= 0
Lobby_Time_Lower 		= 3
Lobby_Time_Upper 		= 10
Global					= 0
Global_Time_Lower		= 3
Global_Time_Upper 		= 10
Side					= 0
Side_Time_Lower 		= 3
Side_Time_Upper 		= 10
Group					= 0
Group_Time_Lower		= 3
Group_Time_Upper		= 10
Vehicle					= 0
Vehicle_Time_Lower 		= 3
Vehicle_Time_Upper		= 10
Command 				= 0
Command_Time_Lower		= 3
Command_Time_Upper 		= 10
Commander 				= 0
Commander_Time_Lower	= 3
Commander_Time_Upper	= 10
Direct 					= 0
Direct_Time_Lower 		= 3
Direct_Time_Upper 		= 10

# Optional
[Reporter]
User 		= name
Password 	= pwd
----------------------------------------------------------
EOF


----------------------------------------------------------
MINIMAL CONFIG FILE EXAMPLE
----------------------------------------------------------
[bec]
Ip			= 127.0.0.1
Port		= 2302
BeBanFile 	= C:\SERVER1\BattlEye\bans.txt
Admins 		= Admins.xml
Commands 	= Commands.xml
----------------------------------------------------------
EOF

# Note that Misc, ChatRestriction, Reporter are all fully optional and does not need to be in the config file.
The only time [Misc] is needed, is if the arma server exe file has been renamed.

Now..
Make a Shortcut to Bec Some place.
Go to properties of this shortcut and edit the Target box, put in the -f argument.
Example!
Target| "c:\..\..\Bec\Bec.exe" -f MyConfig.cfg
Or set up Bec as a service. 







Some explanation of the parameters used by Bec.

------------------------------------------------------------------------------------
* BEC *
------------------------------------------------------------------------------------
In the [Bec] block we define Rcon parameters such as Ip, porta etc. 
All are needed for Bec to work.

-------------------
* Ip = *

The ip Bec need to connect to the server.
By default you should use 127.0.0.1.
But in some cases you need to use other Ip, 
Example if you have 2 servers running on same port and are using multihoming.
if unsure. try with 127.0.0.1 1st

-------------------
* Port = *

The the port the server is running on.

-------------------
* BePath = *

The full path to your Battleye directory for you current profile.
This is the directory where your BEServer.cfg and Bans.txt file is located.

-------------------
* Admins = *

This is the file where you define your admin and the group level on your admins.
This file does not need to be named Admins.xml. but to make it more understandable, we call it Admins.xml for now.
If you do not set full path to this file. it will look in the Config directory 1st.

Valid methods:

Admis = Admins.xml
Admins = C:\some\path\Admins.xml
Admins = \some\path\Admins.xml 

Note. if last method is used. Bec needs to be located on the same partition.

For more information on how to create a admin file, Visit:
Http://ibattle.org/install-and-configure/define-admins/

-------------------
* Commands = *

This is the file where you create your commands.
Set custom names and group level in this file.
This file does not need to be named Commands.xml. but to make it more understandable, we call it Commands.xml for now.
If you do not set full path to this file. it will look in the Config directory 1st.

Valid methods:

Commands = Commands.xml
Commands = C:\some\path\Commands.xml
Commands = \some\path\Commands.xml 

Note. if last method is used. Bec needs to be located on the same partition.

For more information on how to create a command file, Visit:
Http://ibattle.org/install-and-configure/define-commands/





------------------------------------------------------------------------------------
* MISC 
------------------------------------------------------------------------------------
This Block is optional with 1 exception. 
In cases where you have renamed your exe file and need to use ServerExeName = MyNewArmaExeName.exe

-------------------
* AutoLoadBans = *
This parameter defines if you want to automatically run loadbans when ban file(s) changes.
If this parameter is not defined it will be set to off by default.
Use either (False | 0) or (True | 1) as its argument.


-------------------
* Ban = *
This parameter will define if you will ban people for GameHack, BattlEye Hack, Both or No banning at all
You need to specify the value in range 0 til 3

0 = No ban will occure on GameHack or BattlEye Hacks
1 = Will only ban on GameHacks
2 = will only ban BattlEye Hacks
3 = will ban both GameHack and BattlEye Hacks.

Note: If you have a reporter account and use it. you will still report in GameHacks & BattlEye Hacks regardless of your setting.
However, when you check guid's against the database. it will only kick out people according to you setting.
This means, if you have set it to value 1. people caught for battleye hacks will be able to join your server.

If the parameter is not define. Bec will use value 3 as default.

-------------------
* BeCustomBanFiles = *

Set the names of your custom ban files, Separate each file with "," (comma): file1.txt, banfile2.txt, newfile.txt
If you do not use any custom ban files. delete this option or leave this option commented.
This option will check ban files for changes and automatic do a (loadbans file) when a file gets changed

Note: when using this you might also want to use the AutoLoadBans option.

-------------------
* AsciiNickOnly = *

If set to True it will autokick all players who has none ascii chars in the nickname.
Kick happens instant on connect.
If this parameter is not defined, AsciiNickOnly will be set to False by default 

-------------------
* AsciiChatOnly = *

If set to True a warning will be send to the player who does not use Ascii on chat.
You will also need to set parameter Warnings to 0 or higher for this option to work..
If this parameter is not defined, AsciiChatOnly will be set to False by default
Note: This will have no affect on admins, and will be ignored when a admin chats.

-------------------
* IgnoreChatChars = *

This Option will only work if AsciiChatOnly is set on.
Add in chars/symbols that is not listed in the ascii table.
example you don’t want to have/allow german/russian chars. but norwegian is ok for you
then you can do it like.

AsciiChatOnly = True
IgnoreChatChars = æ,Æ,ø,Ø,å,Å

It's recommended that you use a proper editor like Notepad++
When using non ascii chars. you need to save the file with utf encoding.

-------------------
* NickFilterFile = *

Here you can define player names you do not allow on your server.
If a players nick matches any lines in the file he will be autokicked upon connection
If this parameter is not defined, NickFilterFile will be disabled by default
If you do not set full path to this file. it will look in the Config directory 1st.

Valid methods:

NickFilterFile = BadNames.txt
NickFilterFile = C:\some\path\BadNames.txt
NickFilterFile = \some\path\BadNames.txt

Note. if last method is used. Bec needs to be located on the same partition.

-------------------
* WordFilterFile = *

Here you can define words you do not allow on your chat.
If a players chat matches any lines in the file he will be sent a warning.
You will need to set parameter Warnings to 0 or higher for this option to work..
Autokick will happen when he|she reaches the set value..
If this parameter is not defined, WordFilterFile will be disabled by default

Valid methods:

WordFilterFile = BadNames.txt
WordFilterFile = C:\some\path\BadWords.txt
WordFilterFile = \some\path\BadWords.txt

Note. if last method is used. Bec needs to be located on the same partition.

-------------------
* Warnings = *

This is the number of warning a player should get before autokick happens
If example warning is set to 3. the player will get 3 warnings, if he|she still continue to use none ascii after the 3rd warning. he|she will be kicked.

There are 3 functions that uses this parameter.
1 * AsciiChatOnly
2 * WordFilterFile
3 * Warn "command in Commands.xml file"

Example of reply message from Bec:
22:21:24 : (Global) SomeDude:fucking noob.
22:21:25 : RCon admin #0: (To SomeDude) Watch your language. Warnings left:2

Set this to -1 to disable warnings/warnkick functions listed below.
1 * AsciiChatOnly
2 * WordFilterFile
3 * Warn "command in Commands.xml file"

Setting the value to 0 means Instant kick without warning.
the player will then only get a message on the kick reason why kick happened.
Also take a note, the command "warn" in Commands.xml will only work if this value is set higher than 0,
Since there is no point in send a warning when the value is 0 "instant kick". we use !kpl or other names you defined

NOTE: if you do not define this parameter. it will be set to -1 by default. 
	  All 3 depending functions will then be disabled by default.
NOTE: sending a warning to an another admin will not work.

-------------------
* ServerExeName = *

If you for some reason had to rename your Oa/Arma3 server exe file. 
You must use this parameter and set its name. do include the full name inclusive .exe, but not the path.
ServerExeName = myA2Server.exe

-------------------
* ConsoleHeight / ConsoleWidth *


Set the height of Bec's console window
ConsoleHeight = 65

Set the width of Bec's console window
ConsoleWidth = 125


-------------------
* Timeout = *

If your server for some reason needs longer than 30 seconds to start up. 
You can then set custom timeout with this parameter
Timeout = 60
The number is set in seconds.


-------------------
* KickLobbyIdlers = *

Auto kick lobby idlers who take up a slot without playing. lowest timeout is 90 sec. 
if you set this to 0 it will be disabled or if you don’t define this parameter at all it will be ignored.

KickLobbyIdlers = 300
this will kick a player who has been idling in the lobby for 300 sec. 5min
value is set in seconds.

NOTES:
A players is considered to be in the lobby until hes/she is fully ingame.
A player sitting in the briefing screen will be seen as if the player is in the lobby.
A players loading the mission will also be seen as if they are in the lobby.

-------------------
* Scheduler = *

Set the path to your scheduler file.
allows you to create simple schedules.

This is the file where you define your schedules
This file does not need to be named Scheduler.xml.
If you do not set full path to this file. it will look in the Config directory 1st.

Valid methods:

Scheduler = Scheduler.xml
Scheduler = C:\some\path\Scheduler.xml
Scheduler = \some\path\Scheduler.xml 

Note. if last method is used. Bec needs to be located on the same partition.

For more information on how to create schedules, Visit:
Http://ibattle.org/install-and-configure/setting-up-the-scheduler/

Known Issues with the Scheduler. 
* Text containing chars like % @ etc may cause problems. avoid using them for now.

-------------------
* WhiteListFile = *

Set the path to your whitelist file.
In this file you add one guid per line.

Only players who are listed in this file are able to join the server.


Valid methods:

WhiteListFile = whitelist.txt
WhiteListFile = C:\some\path\whitelist.txt
WhiteListFile = \some\path\whitelist.txt

Note. if last method is used. Bec needs to be located on the same partition.

-------------------
* WhileListKickMsg = *

Set custom whitelist kick message. A message must be minimum 7 chars long.

WhileListKickMsg = please connect to our ts3 for more information on howto join. ts3.domain.com


-------------------
* MinPlayerNameLength = *

MinPlayerNameLength = 3
Set the min length a player name can have.
Players connecting with a name shorter than defined in this parameter will be kicked from the server

-------------------
* MaxPlayerNameLength = *

MaxPlayerNameLength = 16
Set the max length a player name can have.
Players connecting with a name longer than defined in this parameter will be kicked from the server.

-------------------
* DisallowPlayerNameChars = *

Limits chars a player can have in the nick
DisallowPlayerNameChars = [](){}<>/\^¨|§!"'#¤%&@£$€
Players that connects and do have any chars in their name that is listed in this parameter will be kicked from the server.

-------------------
* ChatChannelFiles = *

If enabled. it will create additional chat files. once for each channel.
Files will only be created if there is chat in the channels.

-------------------
* SlotLimit = *

If enabled. it will only allow N normal players to join.

Example: 
Using slotlimit 45 on max 90 pl server
-90 players-
90 > 45 ... yes check / kick
------
-75 players-
75 > 45 ... yes check / kick
------
-42 players-
42 > 45 ... no kick.





------------------------------------------------------------------------------------
* Reporting *
------------------------------------------------------------------------------------
In the [Reporter] block we add in account data so that GameHack's|BattlEye Hacks's gets automatically reported to a central ban database.
You will need an account for this to work. 
If you don't have one or don't want to create one, just remove this block since its fully optional.

[Reporter]
User = you
Password = secret


If Enabled it will also check the status on a Guid against the database.
Again this will only work if you have a valid user account..
If you see a file called "Reporting_Failures.log", this is a a fallback file if the host is down or unavailable for some reason.
Do not mess with this file, it will be auto deleted when the bans get uploaded..





------------------------------------------------------------------------------------
* ChatRestriction *
------------------------------------------------------------------------------------
Here you can set max message that is allowed for each channel.
If you want to restrict usage of example global chat.

[ChatRestriction]
Global = 10

This will autokick a player after the 10th message in global channel.
setting the value to 0 mean instant kick..
setting the value to -1 mean its disabled. 

The player will receive  warnings when typing in the global chat

[ChatRestriction]
Global = 10
Side = -1
Group = -1
Vehicle = -1
Command = -1
Commander = -1
Direct = -1

Is the same as 

[ChatRestriction]
Global = 10

So if you don’t need any channels to be restricted. you can delete the hole block [ChatRestriction]
Note: This is will not use the Warnings Parameter for its counter.





------------------------------------------------------------------------------------
* ChatSpam Function *
------------------------------------------------------------------------------------
here you can define the limit for the amount of spam you allow on the server before autokick happens.
Note- the ChatSpam works per chat channel.

each channel has 3 variables.
1st is the channel name
2nd the lower time limit
3rd the upper time limit.

Example: 
Global = 5
Global_Time_Lower = 4
Global_Time_Upper = 10

This will kick a player if he spammed more than 5 lines on the server within 4 secs.
For each line the player spam on the chat when time is less than 4 secs since last line was received the spam-counter increases.
If the player chats between 4 - 10 seconds the spam counter does not increases, but stays at current level.
If the time is greater than 10 sec since last message. the spam counter is reset.

[ChatSpam]
Lobby					= 0
Lobby_Time_Lower 		= 3
Lobby_Time_Upper 		= 10
Global					= 0
Global_Time_Lower		= 3
Global_Time_Upper 		= 10
Side					= 0
Side_Time_Lower 		= 3
Side_Time_Upper 		= 10
Group					= 0
Group_Time_Lower		= 3
Group_Time_Upper		= 10
Vehicle					= 0
Vehicle_Time_Lower 		= 3
Vehicle_Time_Upper		= 10
Command 				= 0
Command_Time_Lower		= 3
Command_Time_Upper 		= 10
Commander 				= 0
Commander_Time_Lower	= 3
Commander_Time_Upper	= 10
Direct 					= 0
Direct_Time_Lower 		= 3
Direct_Time_Upper 		= 10






 ____________________________________________________________________________________
|																					 |
|					  * Understanding the Permission system *						 |
|____________________________________________________________________________________|

Both Admin and the Command must have assigned a group number.
To be able to execute a command. the admin must have the same or a lower group number as the command.

A lower ranked admin can not kick or ban a higher ranked admin..
When i say higher ranked admin.. it means that a admin that has a lower group number than the admin who tried to execute the command.
Equal ranked admins can only kick each other.
When making commands you should consider the level.

*** Short persudo example ***

You may want to use 3 Preset Ban commands and one Kick.
ban for 10min
ban for 60min 
and one ban for PermBan

You may not want all admins to be able to do a permban. but only short bans.
Lets say we have 4 admins and 4 commands.

**************************
# Admins.xml
admin_a - group 0
admin_b - group 1
admin_c - group 2
admin_d - group 1

# Commands.xml
ban_a - group 0 - Perm ban
ban_b - group 1 - 60 min
ban_c - group 2 - 10 min
kick_a - group 3
**************************


# Admin Ban/Kick On ordinary players 
(admin_a) can execute command (ban_a, ban_b, ban_c) on any players 				
(admin_b) can execute command (ban_b, ban_c) on any players						
(admin_c) can execute command (ban_c) on any players
(admin_d) can execute command (ban_b, ban_c) on any players
(admin_a, admin_b, admin_c, admin_d) can execute command kick_a on any players.


# Admins vs Admins
* Kick 
admin_a can execute kick_a on (admin_a, admin_b, admin_c, admin_d)
admin_b can execute kick_a on (admin_b, admin_c, admin_d)
admin_d can execute kick_a on (admin_c, admin_d)
admin_c can only execute kick_a on (admin_c)

Yes you are reading correct. you can kick yourself. ;)
I use this very much for a fast exit, i hate pressing esc. disconnect, disconnect, then esc again.. !kpl in much faster ;D


* Ban
admin_a can execute (ban_a, ban_b, ban_c) on (admin_b, admin_c, admin_d)
admin_b can execute (ban_b, ban_c) on (admin_c)
admin_c can not ban any of (admin_a, admin_b, admin_c, admin_d) due to its lower rank..

Temp Admins may never execute any kick or ban commands on a perm admin.






------------------------------------------------------------------------------------
* Plugins System *
------------------------------------------------------------------------------------

Bec allows you to make your own plugins written in python (g'old 2.6 :)
There is No to Little Documentation on how to create Plugins for Bec.
The best way to learn is to dig through the plugins you find on Ibattle.org download page.
I'll write up the docs about it once i get more time.


To install a Plugins.. 
First step is to create a new directory called Plugins in the root of your Bec install. ( X:\Path\Bec\Plugins )
Next, place your Bec plugin inside the Plugins directory: ( X:\Path\Bec\Plugins\MyPlugin )

Example. lets use the ConnectionLimiter as an example. found at www.ibattle.org on the download page
You should end up with something like.

X:\Path\Bec\Plugins\ConnectionLimiter
X:\Path\Bec\Plugins\ConnectionLimiter\__init__.py
X:\Path\Bec\Plugins\ConnectionLimiter\ReadMe.txt

Thats Basicly it. Next step is to Read the ReadMe file the plugin has. some plugins uses a settings file.. 
So make sure to read the file before starting Bec.






------------------------------------------------------------------------------------
------------------------------------------------------------------------------------
* Basic Rcon Questions..

Q. How do i get a players guid.??
A. You need to type | players | in a Rcon client that accepts command line input.
   You also use the same command to find a players id. "BE id". 
   There are two types of Id's one that Arma will return to you by typing | #userlist |
   This Id is not what you are after when using a RCon. you always want to get the BE_ID instead.
   
Q. How do i Ban a player?
A. first type | players | to get the player BE_ID then execute the command something like this examples.
   assuming the player we want to kick has BE_ID 12
   
   ban 12 				-- > Permban player with BE_ID without reason.
   ban 12 0				-- > Same as above
   ban 12 60 			-- > Ban player with BE_ID 12 without reason for 60 min.
   ban 12 My reason		-- > Permban player with BE_ID 12 and setting reason as "My reason" as the Ban message.
   ban 12 0 My reason	-- > Same as above
   ban 12 60 My reason	-- > Ban player with BE_ID 12 for 60 min and setting reason to "My reason" as the Ban message.
   
   
Q. How do i Kick a player.
A. Same as with Ban. but you do not provide a Time
	assuming the player we want to kick has BE_ID 12
	
	kick 12				-- > Kicks player with BE_ID 12 with no reason set. "default is: Admin Kick" by Battleye
	kick 12 My Reason	-- > Kicks player with BE_ID 12 with reason set as "My reason"
	
Q. How do i remove a ban.
A. First get the Ban index by typing | bans |. locate the ban id in your ban list for the ban you want to remove. 
   Once located you type | removeban Number |.
   
   Another way to do it is by locating you bans.txt file. delete the line containing the baned guid.
   Once removed you can type | loadbans | to reloade the banfile. 
	
	
Q. How do i add a ban on a player thats no longer connected?
A. it basicly works the same wat as ban. but you need to provide the guid instead of the BE_ID.
   examples.
   
   addban abcdef0123456789876543210fedcba9					-- > Permban player with this guid
   addban abcdef0123456789876543210fedcba9 120 "Teamkiller"	-- > Ban player with this guid for 120 min and set reason as Teamkiller
   
For more information use Bis wiki, 
   


