# HTPC
This is me trying to get my dream HTPC setup as functional as possible. Ill hopefully organize this atleast a little bit better soonish.


add F8 as a shortcut to suspend the device
unit files for sleephooks that send 1 (shutdown TV) on sleep and  2 (wake TV up and set source) on resume to /dev/ttyACM0 (or whatever your arduino shows up as)
enable wakeup from the device aswell, so you can turn it on by just turning your TV on

wake from bluetooth and restart bluetooth unit file on resume ( sadly bluetooth connects to my DS4, but the input isnt always recognised after waking by bluetooth, hopefully gonna be fixed with the steam controller 2)
remember to download kodi-addon-peripheral-joystick for arch or the package thats needed for your respective distro.



# KODI
I dont like the idea of needing to switch between apps for different types of media, so KODI seemed like the best choice as its already great for movies, shows, TV and music, so just games needed.
For the people that are fine with multiple apps I recommend looking into KDE Bigscreen and apps like Steam Big picture/ OpengamepadUI and obviously still KODI for watching stuff.
Since playnite has just announced Linux support being planned, this would also be an option.


But for me either the Advanced Kodi Launcher (AKL), or Lutris for Kodi addons seem like a good option. Both do have their respective advantages and problems.
If all you do is play PC games I would just go with Lutris, it allows you to easily manage your games in the Desktop from different launchers, configure wine, gamescope and a lot of different Settings, however currently the addon doesnt creat a lot of folders, no categories (which includes lutris favorites) or recently played. (This is due to the Author relying on lutris -j and -i flags instead of querying the database file directly, categories are just not exposed, and recently played was not added to the Integration yet, when get some more free time I might work on a new Integration that uses the Database direclty, this may also allow adding kodi favorite games to lutris favorite folder automatically.)

AKL is great for all the Retro gamers, and also has recently played games ( I currently dont remember if it has categories, I think so). The biggest downside is that configuring the games is a bit more of a challange, as it all happens within Kodi and is a bit more complicated to set normal games up. 

One thing I am still missing from everything besides Kodi Retroplayer is a Game Overlay, mainly to force quite the game, but being able to adjust other features like a performance overlay or Muting Microphone would be nice.


For Themes a nice one is Arctic Fuse 2, some small annoyances, but quite customizable and supports games.

# Homeassistant
Shelly 4x ble switch and an Internet Controllable AVR togehter with Homeassistant can be nice to control volume and playback stuff, this was basically my workaround to not need to grab the TV remote to change volume, as I couldnt get pipewire to change my AVRs volume directly, nor could I get a good shortcut for the DS4 working that allows me to change the Volume with the controllers.

# History
My cheap SBCs were getting too slow so I finally decided to grab some N100 mini PC for 100€ (still not fast enough to game, but enough for testing).
The problem however was missing CEC, and available Bluetooth Remotes didnt seem satisfactory, Omote got close, but I dont like the screen and its a bit expensive. 
There is the option of Buying a Pulse-Eight USB CEC adapter, which needs way less configuration, but I disliked the Idea of spending money on it, as the firmware is closed source and updates are only available on Windows, so I started to go down the rabbithole of HDMI-CEC at the start of 2025, sadly a lot of links are over 10 years old and expired.
One thing that I wanted from my self made CEC USB adapter is that it keeps the Hardware to a minimum, and to use arduino ide because I am lazy. 

So I made a shitty mix between CEC-TINY-PRO and Pico-CEC with a esp32-S3, which did exactly that. But it couldnt send any data yet, so no turning the TV on or off, this was due to me not really knowing how to code but I did manage to control Kodi so good enough for me.
But I finally decided to continue my quest, so I did what should have been done from the beginning and made the PCB from floe's CEC repo and used the Code from ArduinoLib_CEClient, which has all the functionality I needed to Integrate this properly(ish).



While I was busy with all the CEC stuff, I obviously also explored the extra possibilties with being on an X86 system with a lot more performance, which is mostly gaming, not much to say here as the N100 is too bad to play anything besides stardew valley and Dirt Rally (1), I also did some weird configurations of DS4 controllers to adjust my AVRs volume, that really doesnt work well though. Neither did streaming games loally, gaming worked fine, but the DS4 got confused, espacially with coop games.
