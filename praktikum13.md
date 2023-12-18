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

[int]$aegA = (Get-Date).Millisecond
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

Valjasta 4.1 "Graafikakaardi nimi" ($videoController.Name) 
Valjasta 4.2 "Draiveri versioon" ($videoController.DriverVersion) 
Valjasta 4.3 "Kuupäev" ($videoController.DriverDate)
Valjasta 4.4 "Ekraani lahutus" ((Get-CimInstance Win32_VideoController).CurrentHorizontalResolution, "x", (Get-CimInstance Win32_VideoController).CurrentVerticalResolution)

Valjasta 5.1 "Partitsioonitabel" (Get-CimInstance Win32_DiskPartition | Select-Object -Property DeviceID, Size)
Valjasta 5.2 "Ketta maht" (Get-CimInstance Win32_DiskDrive | ForEach-Object { $_.Size / 1GB })
Valjasta 5.3 "Vaba ruum C: kettal" ((Get-CimInstance Win32_LogicalDisk -Filter "DeviceID='C:'").FreeSpace / 1GB)

Valjasta 6 "" (Get-WmiObject –Class Win32_PnpSignedDriver | Where-Object {$_.DeviceID –like „PCI*“} | Select-Object Description, DriverVersion | Sort-Object Description | Format-Table)
#Tee oma tegevused ja väljasta tulemused funktsiooni abil (võib funktsiooni ise täiendada soovi korral)
#...

#Näidisülesanne:
#$naide = Get-Process | Where-Object { $_.ProcessName -eq "dllhost" }
#Valjasta 2 "NAIDE" (Test-Connection -ComputerName (hostname) -Count 1  | Select IPV4Address)


[int]$aegL = (Get-Date).Millisecond
$ajakulu = ($aegL - $aegA)

Valjasta "*" "TEHTUD" "$ajakulu`n`n"
