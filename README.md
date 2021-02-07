**Repository Moved**

This repository has moved to [tseward/ARSPPM](https://github.com/tseward/ARSPPM).

# ARSPPM
Automated Remote SharePoint Patch Management

A PowerShell module designed to fully patch a SharePoint 2010, 2013, or 2016 farm with minimal administrator interaction. The script has two modes, one for concurrent installation where the farm may be down. The second operating mode is to patch one server at a time, keeping the farm availabile for as long as possible in the case of SharePoint 2010 and 2013, while fully online for SharePoint 2016, given all services are highly availabile within the farm.

Example usage:

    Import-Module .\ARSPPM.psm1
    $cred = Get-Credential #must be a Local/Farm Admin on SharePoint
    $ph = SP01 #This is the host where farm detection takes place and where Content Databases are upgraded
    $patch = "\\fileserver\patches\ubersrvprj2013-kb3114493-fullfile-x64-glb.exe" #UNC to the patch
    Start-RmSPUpdate -StopServices $true -PauseSearch $true -PrimaryHost $ph `
        -ConcurrentPatching $false -Cred $cred -PatchToApply $patch

A process flow diagram is available from the [Wiki](https://github.com/Nauplius/ARSPPM/wiki/Process-Diagram).
