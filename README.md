Progressbar v1.0.0

Free FiveM progress bar resource, supporting ESX / QBCore / Standalone modes.

This version primarily improves compatibility across different server frameworks, suitable for integration with features such as data collection, crafting, repair, lockpicking, and task interaction.

Features

* Supports ESX

* Supports QBCore

* Supports Standalone operation

* Supports automatic framework detection

* Supports NUI progress bars

* Supports animations

* Supports scene actions

* Supports handheld props

* Supports freezing the player

* Supports canceling the progress bar

* Compatible with older versions of the `progressBars:startUI` call

* Compatible with common QBCore progressbar call methods

* Fixed fetch issues caused by hardcoding resource names in NUI

* Automatically cleans up animations and props when resources stop

Installation Method

1. Download the compressed package at the bottom of this page

2. Extract the package and place it in the server's `resources` folder

3. It is recommended to name the folder:

`progressbar`

4. Add the following to `server.cfg`:

`ensure progressbar`

Configuration Instructions

Framework mode can be set in `config.lua`:

`Config.Framework =` 'auto'

Optional:

'auto'
'esx'
'qb'
'standalone'

The default recommended setting is 'auto', which will automatically detect the framework currently being used by the server.

Usage Examples

Legacy progressBars Call

TriggerEvent('progressBars:startUI', 5000, 'Processing...')

Export Call

exports['progressbar']:startUI(5000, 'Processing...')

ESX Style Call

exports['progressbar']:Progressbar("Processing...", 5000, {
FreezePlayer = true,
animation = {
type = "anim",
dict = "amb@world_human_hammering@male@base",
lib = "base"

},
onFinish = function()
print("Completed")
end,
onCancel = function()
print("Canceled")
end
})

QBCore Style Call

exports['progressbar']:Progress({
name = "example_action",
duration = 5000,
label = "Processing...", useWhileDead = false,

canCancel = true,

controlDisables = {

disableMovement = true,

disableCarMovement = true,

disableMouse = false,

disableCombat = true,

},

anim = {

animDict = "amb@world_human_hammering@male@base",

anim = "base",

flags = 49,

},

}, function(cancelled)

if not cancelled then

print("Completed")

else

print("Cancelled")

end
end)

Dependencies

No mandatory dependencies.

Optional frameworks:

* es_extended

* qb-core

If the server does not have ESX or QBCore installed, it can also run as a standalone resource.

Important Notes

It is recommended not to change the resource folder name; keep it as:

progressbar

Because many FiveM scripts use by default:

exports['progressbar']

If you change the folder name, the export calls in other scripts also need to be modified accordingly.

Update Content

v1.0.0

* Initial free release

* Added ESX / QBCore / Standalone compatibility

* Added automatic framework detection

* Added compatibility with the old version of progressBars:startUI

* Fixed NUI resource name hardcoding issue

* Optimized animation, Prop, Cancel, and resource stop cleanup logic

Declaration

This resource is released free of charge for the FiveM community.

Personal servers are allowed to use it for free and modify it.

Please do not resell, resell, or sell it as original content.
