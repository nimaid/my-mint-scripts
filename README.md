# my-mint-scripts
A place for me to store the custom /usr/local/bin/ scripts I write for my Mint 19 Cinnamon. It's mainly just so I can easily install them via a shell. If you want to use them, you may need to tweak them a bit for your setup. Here be dragons.



## anonymine
### No arguments.
This just connects you to the anonymine server through ssh. Enjoy a game of minesweeper in ASCII wonder!


## listdisplays
### No arguments.
This lists the connected displays with xrandr. Use this to customize setbright and setgamma to your setup.

##remove-cdrom-sources
### No arguments
This removes any lines containing the string "cdrom" from "/etc/apt/sources.list". This is useful for a persistent live Mint install, as on each reboot it adds a cdrom deb that breaks apt.
I suggest adding a cron entrt to run it at boot (after it has just been added :p)
> @reboot sudo runuser -l mint -c "remove-cdrom-sources"

## setbright
### Argument 1: Brightness (1.0 = normal)
Uses xrandr to set the brightness of my displays. Run listdisplays to get the info to customize it.


## setgamma
### Argument 1: Red Gamma (1.0 = normal)
### Argument 2: Green Gamma (1.0 = normal)
### Argument 3: Blue Gamma (1.0 = normal)
Uses xrandr to set the RGB gamma of my displays. Run listdisplays to get the info to customize it.


## setredbright
### Argument 1: Brightness (1.0 = normal)
### Argument 1: Green/Blue Gamma (1.0 = normal, go lower to make more red)
Uses xrandr to set the brightness and "red-ness" of my displays. Run listdisplays to get the info to customize it.


## setwallpaper
### Argument 1: Image (Absolute path required!)
Uses gsettings to change the Cinnamon background to the specified file.


## updatewallpaper
### Argument 1 (Optional): Manual Time Override (0-23)
Uses setwallpaper and date to set a background appropriate for the time of day. Change the MORNING, DAY, EVENING, and NIGHT variables (must be absolute paths!) to your favorite timed wallpaper set.
I also suggest adding cron entries to run at boot and every hour, so that your wallpaper automagically updates. Here's what my working entries look like:
> @reboot sudo runuser -l mint -c "updatewallpaper"

> 0 * * * * sudo runuser -l mint -c "updatewallpaper"


## windows_sethc_backdoor
### Argument 1: Target drive (like /dev/sda4)
### Argument 2 (Optional): Executable name (defaults to "sethc", but "Utilman" is good for newer Windows)
Installs a physical access backdoor on a Windows NT drive that gives you an admin command prompt at the login screen if you press shift 5 times. This is for the IT work I do, it is useful to reset peoples passwords using a Live USB and "net user".
If you do something dumb with this, it's your fault. I provide this script "as is" with no warranty, and no not take responsibility for how it is used by others.
