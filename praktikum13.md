#$nr:	küsimuse number
#$param: mis parameetriga tegemist (võimalikult lühidalt)
#$sisu:	väljastatav sisu
function valjasta{
	param ($nr, $param, $sisu)
	$fail = ".\tulemus.txt"
	$aeg = Get-Date -Format "HH:mm:ss.fff"
	if($sisu -eq $null){
		$rida = "$nr.	$aeg	${param}:	NULL"
		Write-Output $rida
		$rida | Out-File -FilePath $fail -Append
	}elseif($sisu.GetType().Name -eq "Object[]"){
		$rida = "$nr.	$aeg	${param}:"
		Write-Output $rida $sisu
		$rida | Out-File -FilePath $fail -Append
		$sisu | Out-File -FilePath $fail -Append
	}else{
		$rida = "$nr.	$aeg	${param}:	$sisu"
		Write-Output $rida
		$rida | Out-File -FilePath $fail -Append
	}
}

$failiTee = "$env:USERPROFILE\valjund.txt"
Start-Transcript -Path $failiTee -Append

[int]$aegA = (Get-Date).Millisecond

try {
    $ErrorActionPreference = 'SilentlyContinue'
    Valjasta 0 "ALGUS" ("Aeg: "+(Get-Date -Format "dddd MM/dd/yyyy HH:mm K")+" Teostaja: Erkki")
    Valjasta 1.1 "host" (hostname)
    Valjasta 1.2 "PowerShelli versioon" ($PSVersionTable.PSVersion)
    Valjasta 1.3 "Windowsi versioon" ((Get-CimInstance Win32_OperatingSystem).Version)

    Valjasta 2.1 "Ip-aadress" ((Get-NetIPAddress -AddressFamily IPv4).IPAddress)
    Valjasta 2.2 "Võrgumask" (Get-NetIPAddress | Where-Object {$_.AddressFamily -eq 'IPv4'}).PrefixLength
    Valjasta 2.3 "Gateway" ((Get-NetRoute "0.0.0.0/0").NextHop)
    Valjasta 2.4 "DHCP" ((Get-NetIPConfiguration | Select-Object -ExpandProperty NetIPv4Interface).Dhcp)
    Valjasta 2.5 "MAC-aadress" ((Get-NetAdapter | Where-Object { $_.Status -eq 'Up' }).MacAddress)

    Valjasta 3.1 "Protsessori kirjeldus" ((Get-CimInstance Win32_Processor).Caption)
    Valjasta 3.2 "RAM kogus" ((Get-CimInstance Win32_ComputerSystem).TotalPhysicalMemory / 1GB)

    Valjasta 4.1 "Graafikakaardi nimi" (Get-CimInstance Win32_VideoController).Caption 
    Valjasta 4.2 "Draiveri versioon" (Get-CimInstance Win32_VideoController).DriverVersion
    Valjasta 4.3 "Kuupäev" (Get-CimInstance Win32_VideoController).DriverDate
    Valjasta 4.4 "Ekraani lahutus" ((Get-CimInstance Win32_VideoController).CurrentHorizontalResolution, "x", (Get-CimInstance Win32_VideoController).CurrentVerticalResolution)

    Valjasta 5.1 "Partitsioonitabel" (Get-CimInstance Win32_DiskPartition | Select-Object -Property DeviceID, Size)
    Valjasta 5.2 "Ketta maht" (Get-CimInstance Win32_DiskDrive | ForEach-Object { $_.Size / 1GB })
    Valjasta 5.3 "Vaba ruum C: kettal" ((Get-CimInstance Win32_LogicalDisk -Filter "DeviceID='C:'").FreeSpace / 1GB)

    Valjasta 6 "Draiverite info" (Get-WmiObject –Class Win32_PnpSignedDriver | Where-Object {$_.DeviceID –like "PCI*"} | Select-Object Description, Manufacturer, DriverVersion | Sort-Object Description | Format-Table)

    Valjasta 7 "Kasutajad" (Get-WmiObject Win32_UserAccount | Select-Object Name, Description, LocalAccount, Disabled | Format-Table)

    Valjasta 8 "Käimasolevate protsesside arv" ((Get-Process).Count)

    Valjasta 9 "10 viimasena käivitatud protsessi" (Get-Process | Sort-Object StartTime -Descending | Select-Object -First 10 Name, Id, StartTime | Format-Table)

    Valjasta 10 "Kuupäev ja kellaaeg" (Get-Date)
}
finally {
    $ErrorActionPreference = 'Continue'
}

[int]$aegL = (Get-Date).Millisecond
$ajakulu = ($aegL - $aegA)

Valjasta "*" "TEHTUD" "$ajakulu`n`n"

Stop-Transcript



# Faili tee seadmine:

$failiTee = "$env:USERPROFILE\valjund1.txt" -Tee failile, kuhu skript salvestab väljundi.
Start-Transcript -Path $failiTee -Append -Alustab skripti jooksul transkriptsiooni, salvestades käsurea väljundi faili.


# Try-blokk:

try-finally blokk tagab, et isegi kui midagi läheb valesti (try-plokis), taastatakse ErrorActionPreference väärtus lõpuks (finally-plokis). Lisasin selle, kuna punktis 9 oli mitmetele protsesside algusajale ligipääs keelatud.

# info kogumine:
Skript kogub mitmesugust süsteemiinfot ja väljastab selle funktsiooni valjasta abil:

    Get-CimInstance: See käsustik tagastab Windows Management Instrumentation (WMI) objektide eksemplarid.
    Get-NetIPAddress: Tagastab võrgu liideste IP-aadressid.
    Get-NetRoute: Tagastab võrgu marsuudid.
    Get-NetIPConfiguration: Tagastab võrgu liideste IP-konfiguratsiooni.
    Get-NetAdapter: Tagastab võrguadapterite info.
    Get-Process: Tagastab käimasolevate protsesside info.
    Get-WmiObject: Tagastab WMI objektide info.

Stop-Transcript: Lõpetab transkriptsiooni, salvestades kogu skripti väljundi faili.

[valjund.txt](https://github.com/Marten221/opsys_Ojasaar/files/13709084/valjund.txt)
