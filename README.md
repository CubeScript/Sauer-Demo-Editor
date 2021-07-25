# Cube 2 Sauerbraten Pseudo Demo Editor
A menu for [Sauerbraten](http://sauerbraten.org) with functions to execute client commands at a specific time of a demo (replay), as well as functions to rewind and fast forward.

### Installation
1. Download the [demoeditor.zip](https://github.com/SalatielSauer/Sauer-Demo-Editor/releases/latest) (without extracting it).
2. Move it to the root folder of your Sauerbraten (the home folder or the main installation folder).
3. Find your autoexec.cfg file or create a new one (also in one of the root folders), open it in a text editor and add the two commands:<br>
  `addzip demoeditor.zip; exec demoeditor.cfg`<br>
    The zip will be extracted internally and the configuration file (demoeditor.cfg) will be applied whenever you start the game.

To open the menu you can either type `/demoeditor` in the game's chat console (T key by default), or add an "edit" argument to the demo command (`/demo anydemoname edit`).

Alternatively to step 3 you can type the command `/notepad autoexec.cfg` during the game to open the built-in text editor.

### Tools
<img src="packages/icons/de_skip_left.png" width="16px"/><img src="packages/icons/de_skip_right.png" width="16px"/> **Rewind and Fast-forward**:<br>
You can use the arrow icons to control the current remaining time, and the gray sum/minus icons to control the selected target time.<br>
![](https://raw.githubusercontent.com/SalatielSauer/misc/master/demoeditor_fastforward_rewind.gif)<br>
The colors of the arrows represent a state:<br>
- Invisible: Current remaining time equals selected time
- Gray: Unable to rewind/forward
- Orange: Able to rewind/forward<br>

<img src="packages/icons/de_plus.png" width="16px"/> **Adding Actions**:<br>
You can use the green sum icon to add actions to the current project, just select the time you want and fill the text field with any command.<br>
![](https://raw.githubusercontent.com/SalatielSauer/misc/master/demoeditor_add_actions.gif)<br>

<img src="packages/icons/de_gear.png" width="16px"/> **Starting Actions**:<br>
Actions are not executed by default, you can enable or disable them using the gear icon.<br>
![](https://raw.githubusercontent.com/SalatielSauer/misc/master/demoeditor_start_actions.gif)<br>
Each color of the gear represents a state:<br>
- Gray: Actions are disabled and game is paused
- Yellow: Actions are enabled and game is paused
- Red: Actions are disabled and game is running
- Green: Actions are enabled and game is running<br>

<img src="packages/icons/de_minus.png" width="16px"/> **Removing Actions**:<br>
You can use the red minus icon to remove individual actions, or the gear icon submenu to remove all actions.<br>
![](https://raw.githubusercontent.com/SalatielSauer/misc/master/demoeditor_remove_actions.gif)<br>

<img src="packages/icons/de_folder.png" width="16px"/> **Saving and Loading Actions**:<br>
The folder icon allows you to save or load actions from an external (.cfg) file.<br>
![](https://raw.githubusercontent.com/SalatielSauer/misc/master/demoeditor_save_load_actions.gif)<br>
The demo/project name is added automatically, if no path is specified, the .cfg file will be saved in the $demodir, next to the .dmo file.<br>
The colors of the save button also represent a state:<br>
- Red: The specified demo name does not exist
- Yellow: There is already a .cfg file available with the demo name
- White: The demo exists and there is no .cfg file available

If you prefer, you can edit the actions configuration file manually following this structure:
```
_de_echo [Loaded 3 actions by unnamed]
_de_actions_time = [[540] [480] [443]]
_de_actions_timereadable = [[9 0] [8 0] [7 23]]
_de_actions_command = [[echo "action 1"] [echo "action 2"] [echo "action 3"]]
```
For an action file to be automatically detected when loading a demo, it must be in the same folder and have the same name as the .dmo.
If you want to load an action file manually, just apply the file with `/exec actionfile.cfg` or change the project name using the interface.