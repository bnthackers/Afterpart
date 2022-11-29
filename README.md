
![AfterPart v1.0](Cheese_Sat-07Dec19_17.19.png)
<br>



   /_\  / _| |_ ___ _ _| _ \__ _ _ _| |_ 
  / _ \|  _|  _/ -_) '_|  _/ _` | '_|  _|
 /_/ \_\_|  \__\___|_| |_| \__,_|_|  \__|
                                            

    Version release: v1.0 (Stable)
    Author: Garvit Sharma, Shivam Kumar, Gaurav Anjna [ G-S-G ]
    Distros Supported : Linux Ubuntu, Kali, Mint, Parrot OS

## Legal Disclamer:
    The author does not hold any responsibility for the bad use of this tool,
    remember that attacking targets without prior consent is illegal and punished by law.

<br /><br />

## Description:
    This module takes one existing image.jpg and one payload.ps1 (input by user) and
    builds a new payload (agent.jpg.exe) that if executed it will trigger the download of
    the 2 previous files stored into apache2 (image.jpg + payload.ps1) and execute them.

    This module also changes the agent.exe Icon to match one file.jpg Then uses the spoof
    'Hide extensions for known file types' method to hidde the agent.exe extension.

    All payloads (user input) will be downloaded from our apache2 webserver
    and executed into target RAM. The only extension (payload input by user)
    that requires to write payload to disk are .exe binaries.
 
## Exploitation:
    ImgBackdoor stores all files in apache2 webroot, zips (.zip) the agent,
    starts apache2 and metasploit services(handler), and provides a URL to send to
    target (triggers agent.zip download). As soon as the victim runs our executable,
    our picture will be downloaded and opened in the default picture viewer, our
    malicious payload will be executed, and we will get a meterpreter session.

    But it also stores the agent (not ziped) into ImgBackdoor/output folder
    if we wish to deliver agent.jpg.exe using another diferent attack vector.

    'This tool also builds a cleaner.rc file to delete payloads left in target'




## Download/Install/Config:
    1 - Download framework from github
         git clone https://github.com/Tsuyoken/ImgBackdoor

    2 - Set files execution permitions
         cd ImgBackdoor
         sudo chmod +x *.sh

    3 - Config ImgBackdoor settings
         nano settings

    4 - Run main tool
         sudo ./AfterPart
