M2 — Create an Azure Availability Set with PowerShell

Objective

Create an Azure Availability Set using the Azure PowerShell module.

Configuration

Name: as-m2-northeu

Resource group: rg-m1-ps-northeu

Region: northeurope

SKU: Aligned

Fault domains: 2

Update domains: 5

PowerShell

$availabilitySetName = "as-m2-northeu"

New-AzAvailabilitySet `
    -ResourceGroupName "rg-m1-ps-northeu" `
    -Name $availabilitySetName `
    -Location "northeurope" `
    -PlatformFaultDomainCount 2 `
    -PlatformUpdateDomainCount 5 `
    -Sku "Aligned"

Verification

Get-AzAvailabilitySet `
    -ResourceGroupName "rg-m1-ps-northeu" |
    Select-Object Name, Location, Sku,
        PlatformFaultDomainCount,
        PlatformUpdateDomainCount

Result

The Availability Set was created and verified successfully.

No virtual machines are currently attached to this Availability Set.

What I learned

An Availability Set helps improve virtual machine availability by distributing VMs across fault domains and update domains. The Availability Set itself does not create virtual machines.
