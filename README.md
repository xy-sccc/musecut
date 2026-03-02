# Music-shortcut

A customized key shortcut for music lovers to open music apps whenever they want

Hello people, this simple automation allows users to open music applications quickly with simple key combos. It is beginner-friendly and does not require any coding experience. Simply follow the following steps to make this happen on your laptop!!!

This guide helps you create a keyboard shortcut on macOS that:
- Opens Apple Music
- Brings it to the front
- Shows it in a small window (not full screen)

Contact: Reach out to sunchxy@gmail.com if you encounter any issues during the installation. 

------------------------------------------------------------------------------------------------------------

Step 1: 
- Open TextEdit.
- Click Format in the top menu, then Make Plain Text.
- Copy and paste this script exactly below

------------------------------------------------------------------------------------------------------------
```
-- Mini player launcher for Apple Music (macOS)
-- Trigger this script with a keyboard shortcut (Automator/Shortcuts/Alfred/etc.)

property appName : "Music"
property windowX : 120
property windowY : 90
property windowW : 980
property windowH : 640

on run
    tell application appName
        activate
        reopen
        delay 0.35

        -- Some states need a second reopen before a browser window appears.
        if (count of windows) is 0 then
            reopen
            delay 0.35
        end if

        if (count of windows) > 0 then
            try
                set miniaturized of front window to false
            end try
            try
                set collapsed of front window to false
            end try
            try
                set index of front window to 1
            end try
            try
                set bounds of front window to {windowX, windowY, windowX + windowW, windowY + windowH}
            end try
        end if
    end tell
end run
```
------------------------------------------------------------------------------------------------------------

Step 2: 
- Save the file as: /Users/xxxx/Documents/Playground/apple-music-mini-window.applescript
- xxxx is dependent on your username

------------------------------------------------------------------------------------------------------------

Step 3: 
-  Open Automator.
- Click New Document.
- Choose Quick Action.
- At the top:
  Set Workflow receives to no input
  Set in to any application
- In the left search bar, type Run AppleScript.
- Drag Run AppleScript into the workflow area.
- Delete default text and paste the command below

------------------------------------------------------------------------------------------------------------
```
run script (POSIX file "/Users/scxy/Documents/Playground/apple-music-mini-window.applescript")
```
------------------------------------------------------------------------------------------------------------

- Save it as: Mini Music Window.
- Open System Settings → Keyboard → Keyboard Shortcuts.
- Go to Services (or Quick Actions), find Mini Music Window, and assign your key combo.

------------------------------------------------------------------------------------------------------------

Now you are offically done!!! Test with your new shortcut: control+option+command+left_arrow

Note: 
- If you see something like “Automator workflow runner is not allowed…”, do this:

Open System Settings → Privacy & Security → Automation.
Allow Automator or WorkflowRunner to control Music.
Open Privacy & Security → Accessibility.
Enable Automator or WorkflowRunner if listed.

- If App Opens but No Window Appears

Right-click Music in Dock → Options → Assign To → choose None.
Check other desktops/spaces in Mission Control.
In Music menu bar, click Window → Bring All to Front

------------------------------------------------------------------------------------------------------------

How to Switch to Spotify?

In the script file, change this line:
```
property appName : "Music"
```
and swithc to 
```
property appName : "Spotify"
```
This is the only line needed to be changed, do not adjust anything else

------------------------------------------------------------------------------------------------------------

How to Change window size? 

In the script file, change this line: 
```
property windowX : 120
property windowY : 90
property windowW : 980
property windowH : 640
```

The X and Y values are indication of where the window will appear, the W and H values are the size of the window. Adjust based on your need. Only change the numerical value, do not change any parts of the command.

------------------------------------------------------------------------------------------------------------

I am so happy that you've finished all the step, enjoy your music!!! 
~ Spaghattii, eat it up eat it eat it up ~ 

