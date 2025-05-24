Collection of scripts and notes for how I customize Termux on my devices. Intended to be limited to things unique to integrating with the Android environment and applications (rather than typical Unix/Linux customization)

intents.txt notes on how to send an intent into Termux in order to run a shell script, python script, or anything else.

macrodroid/termux-script.macro an exported macro from Macrodroid that implements the above intent and lets Macrodroid run a Termux program (script or binary) as an Action. I use this to run an rsync job every night.

bin/termux-script.sh example script that the above Macrodroid intent example will run. this particular script does nothing, but in my setup, I have it run an rsync job to back up my phone to my personal server.

bin/my-source-ssh-agent copy of "source-ssh-agent" that used to be distributed with the openssh Termux package. It's intended to be sourced (i.e. ". my-source-ssh-agent") in a .bashrc or any shell script, in order to conditionally start, add keys to, and use ssh-agent. It works regardless of whether you choose to run ssh-agent at device startup. 

bin/termux-file-editor This script will get run every time you share a file to Termux. The script is written so that it can process an arbitrary number of files, although apparently there is no way to make Termux accept multiple shared files at once. Note that before running this script, Termux will first pop up a GUI prompting you to download the file into a directory called ~/downloads/. Confusingly, you need to tap "Edit" to cause the script to run. Note that the files will remain in ~/downloads/ so you should delete them in your script, if you don't want them to accumulate. I use this script to run secure copy on the files to my personal server. Now when I Share single files to Termux, it easily uploads them to my personal server with having to drop to the command line.
