# 🎨 PowerShell Profile forked from [Chris Titus Tech's PowerShell Profile](https://github.com/ChrisTitusTech/powershell-profile)

A stylish and functional PowerShell profile that looks and feels almost as good as a Linux terminal. And keep all good commands and functions from the old version, but with some customizations from me.

## ⚡ One Line Install (Elevated PowerShell Recommended)

Execute the following command in an elevated PowerShell window to install the PowerShell profile:

```
irm "https://github.com/harrytien107/powershell-profile/raw/main/setup.ps1" | iex
```

## 🛠️ Fix the Missing Font

After running the script, you'll have two options for installing a font patched to support icons in PowerShell:

### 1) You will find a downloaded `cove.zip` file in the folder you executed the script from. Follow these steps to install the patched `Caskaydia Cove` nerd font family:

1. Extract the `cove.zip` file.
2. Locate and install the nerd fonts.

### 2) With `oh-my-posh` (loaded automatically through the PowerShell profile script hosted on this repo):
1. Run the command `oh-my-posh font install`
2. A list of Nerd Fonts will appear like so:
<pre>
PS> oh-my-posh font install

   Select font

  > 0xProto
    3270
    Agave
    AnonymousPro
    Arimo
    AurulentSansMono
    BigBlueTerminal
    BitstreamVeraSansMono

    •••••••••
    ↑/k up • ↓/j down • q quit • ? more</pre>
3. With the up/down arrow keys, select the font you would like to install and press <kbd>ENTER</kbd>
4. DONE!
   
## Customize this profile

**Do not make any changes to the `Microsoft.PowerShell_profile.ps1` file**, since it's hashed and automatically overwritten by any commits to this repository.

After the profile is installed and active, use these two layers:

1) `profile.ps1` (override layer created via `Edit-Profile`)
- Use this file to override variables/functions exposed by the base profile.

2) `CTTcustom.ps1` (personal custom layer loaded at startup)
- Use this file for personal PATH exports, aliases, and theme overrides.
- This file is intended to stay local and survive upstream profile updates.

### CTTcustom.ps1 example

```powershell
# Example: custom oh-my-posh theme
oh-my-posh init pwsh --config "https://github.com/JanDeDobbeleer/oh-my-posh/raw/refs/heads/main/themes/1_shell.omp.json" | Invoke-Expression

# Example: custom PATH additions
$env:Path += ";D:\CODE\PowerShell-plugin\devtidy_Windows_x86_64"
```

THE FOLLOWING VARIABLES RESPECT _Override:
<pre>
$EDITOR_Override
$debug_Override
$repo_root_Override  [To point to a fork, for example]
$show_help_Override  [display Show-Help on PowerShell launch]
$timeFilePath_Override
$updateInterval_Override
$autoUpdateProfile_Override [auto-run Update-Profile on launch]
$autoUpdatePowerShell_Override [auto-run Update-PowerShell on launch]
</pre>

THE FOLLOWING FUNCTIONS RESPECT _Override: _(do not call the original function from your override function, or you'll create an infinite loop)_
<pre>
Debug-Message_Override
Update-Profile_Override
Update-PowerShell_Override
Clear-Cache_Override
Get-Theme_Override
WinUtilDev_Override [To call a fork, for example]
Set-PredictionSource_Override
</pre>
