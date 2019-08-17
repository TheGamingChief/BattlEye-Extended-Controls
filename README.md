# BattlEye-Extended-Controls

BattlEye-Extended-Controls (BEC) is a program created by nuxil/Stian Mikalsen. This utility was created for ArmA 2 and ArmA 3 to take advantage of the Rcon protocol and provide tools for game server owners and administrators. BEC while originally made for ArmA 2 and ArmA 3 still works just fine for DayZ SA since the Rcon protocol has not changed much.

## Installation

Installation of BEC is rather simple, download this repository and create a BEC folder somewhere on the machine that is hosting your server. Then copy all the files included in the download into your new BEC folder.

Once everything is copied into your new BEC folder you will need to open the Config folder included, and navigate to the Config.cfg file. You MUST change the BePath to match up with your Battleye directory.

You will also need to add the following lines to the end of your hosts file. More information and instructions on how to do this can be found [here](https://github.com/TheGamingChief/BattlEye-Extended-Controls/blob/master/How%20to%20edit%20hosts%20file.txt).

```bash
127.0.0.1 ibattle.org
127.0.0.1 www.ibattle.org
```
Note:
If you have not created a bans.txt file in your Battleye directory you will see [this](https://i.imgur.com/bJkWRRx.jpg) error while trying to start BEC. You must create a bans.txt file in your Battleye directory to make this error go away.

## Implementation

There are several different ways to implement BEC into your current Start Server batch file.

Method #1 (Recommended):

Use one single batch file that updates your DayZ server, starts your DayZ server, starts BEC, and checks for server/BEC crashes. An example of a single batch file that accomplishes all of this at once is available [here](https://pastebin.com/yHgZLT4b). Keep in mind there are several things you will need to change in that batch file to suit your own environment, most notably lines 5, 7, 8, 9, and 65. If you have issues using this batch file I recommend you watch my video where I go over this [here](https://youtu.be/IrIEj6o9YoM).

Method #2 (Not Recommended):

Another method of starting BEC would be to create your own batch file (or include it in your start-server batch file) to starts BEC. Please keep in mind when starting BEC.exe you need to use the -f Config.cfg --dsc flags. An example of this is below.

```
cd "C:\Servers\BEC"
start Bec.exe -f Config.cfg --dsc
```

Method #3 (Really Not Recommended):

You can also choose to run BEC manually if you wanted to do this for some odd reason. However, you can not just run the BEC.exe because you need to run it with the -f Config.cfg --dsc flags. This can be achieved by creating a shortcut of BEC.exe and adding those flags so your shortcut looks something like [this](https://i.imgur.com/8jhwW7P.jpg).

## The Scheduler
The Scheduler is an extremely powerful tool that comes with BEC. This tool allows you to schedule tasks such as automated messages, automated shutdown, ETC. The Scheduler is configured via the Scheduler.xml file.

This scheduler is currently set up to shut down the server at 12 AM and 12 PM local time. This is when the batch file used in Method #1 of Implementation would restart the server again. The Scheduler is also currently configured to send out messages to the server warning everyone the server is restarting in 2 hours, 1 hour, 30 minutes, 20 minutes, 15 minutes, 10 minutes, 5 minutes, 3 minutes, 1 minute, and seconds before the server shuts down. The current scheduler is also configured to warn the server every 45 minutes of the servers restart schedule. 

This is of course all configurable, there is a sample scheduler named Scheduler - Example.xml which has some examples on how the scheduler can be used. There is also Scheduler-FAQ.txt which has a bunch of important information pertaining to the scheduler.

Please make sure to update tests as appropriate.

## Credits/License
[nuxil/Stian Mikalsen](https://forums.bohemia.net/profile/737210-nuxil/)

[License](https://github.com/TheGamingChief/BattlEye-Extended-Controls/blob/master/LICENSE.txt)
