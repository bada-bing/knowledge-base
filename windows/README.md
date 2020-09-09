# Windows
- [TIP.1] How to open always an app on the same monitor all the time
	- Open the application, drag it to the screen you want it to open on, minimize it to half size (the middle square shape on the top far right - beside the X (ie, close button)) and then close it out without maximizing it again.
	From now on it will open on that screen, until you change it by repeating this process on a different screen.

## Powershell and CMD
- print "path" variable in cmd: ```path```; in powershell: ```$env:path```

- How to run powershell script (ps1): [SO Link](https://stackoverflow.com/questions/2035193/how-to-run-a-powershell-script/2035209)

- [How to **kill a service**](https://support.4it.com.au/article/how-to-kill-a-windows-service-which-is-stuck-at-stopping/)
  - find PID of service:  `sc queryex servicename`
  - shutdown service: `taskkill /f /pid [PID]`
- Copying to Clipboard
	in WSL you can do `clip.exe < ~/.ssh/some_file` or `cat ~/.ssh/some_file | clip.exe`
## Windows Terminal
- [setting-up-the-new-windows-terminal](https://www.luminate.one/blog/setting-up-the-new-windows-terminal)
- [customizing-WT](https://www.howtogeek.com/426346/how-to-customize-the-new-windows-terminal-app/)
- how to add gitbash to WT [SO link](https://stackoverflow.com/questions/56839307/adding-git-bash-to-the-new-windows-terminal)
- [Ideas for configuring WT](https://gist.github.com/bitcrazed/e906376cd895364410a8280fdcd30a50)


How to find MS directories:
`ms-appdata:/…:` - should be mapped to something like `C:\Users\mpetkovic\AppData\Local\Packages\Microsoft.WindowsTerminal_8wekyb3d8bbwe`
ms-appx:/

`ms-appx` is your app package (where the app is installed), and `ms-appdata` is your application data.

[Rearange Windows in Win 10 Keyboard Shortcuts](https://www.howtogeek.com/661249/how-to-rearrange-windows-with-keyboard-shortcuts-on-windows-10/)

Open new Instance of Ubuntu in the src/ folder: `wt.exe -d c:\Users\mpetkovic\src -p "Ubuntu"`
