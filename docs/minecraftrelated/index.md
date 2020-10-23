# Minecraft Related
## Ask for filename and if it's equal to server.jar run it as a minecraft server -_- BitsTransfer - minecraft. Code:
```powershell
$url = Read-Host -Prompt 'input link'
$output = Read-Host -Prompt 'input destinationfolder'
$name = Read-Host -Prompt 'input filename'
$start_time = Get-Date

Import-Module BitsTransfer
Start-BitsTransfer -Source $url -Destination $output

Write-Output "Time taken: $((Get-Date).Subtract($start_time).Seconds) second(s)"

if($name -eq 'server.jar'){
    cd $output
    java -Xmx1024M -Xms1024M -jar server.jar nogui | Out-Null
    $file = $output + '\eula.txt'
    ((Get-Content -path $file -Raw) -replace 'false','true') | Set-Content -Path $file
    $file2 = $output + '\Start.cmd'
    New-Item -Path $file2 -ItemType File
    Set-Content -Path $file2 -Value 'java -Xmx1024M -Xms1024M -jar server.jar nogui'
    java -Xmx1024M -Xms1024M -jar server.jar nogui
}
```
## Always run as a minecraft server -_- get_a_normal_minecraft_server_easily - BitsTransfer. Code:
```powershell
$url = 'https://launcher.mojang.com/v1/objects/f02f4473dbf152c23d7d484952121db0b36698cb/server.jar'
$output = Read-Host -Prompt 'input destinationfolder(remember every folder has to exist already)'
$start_time = Get-Date

Import-Module BitsTransfer
Start-BitsTransfer -Source $url -Destination $output

Write-Output "Time taken: $((Get-Date).Subtract($start_time).Seconds) second(s)"

cd $output
java -Xmx1024M -Xms1024M -jar server.jar nogui | Out-Null
$file = $output + '\eula.txt'
((Get-Content -path $file -Raw) -replace 'false','true') | Set-Content -Path $file
$file2 = $output + '\Start.cmd'
New-Item -Path $file2 -ItemType File
Set-Content -Path $file2 -Value 'java -Xmx1024M -Xms1024M -jar server.jar nogui'
java -Xmx1024M -Xms1024M -jar server.jar nogui
```
