# Appviewx SaaS Portal Beta

> ADC+ Appviewx SaaS beta
> https://ingrammicro-try.appvx.com/appviewx/login



* `Use Cases`:

  * F5 device upgrades & CVE Reporting  
  * Canary-Based Deployment  
  * Build and Application View of New Load Balancing Services  
  * Golden Config Compliance  
  * Blue-Green Based Deployment  
  * Visibility into Brownfield Infrastructure  
  * LBaaS (Load Balancing as a Service) across hybrid infrastructure  
  * Certificate Management on F5s (and other network components)  

  
* `Workflows - Notes` 

## Configuration Management  

* `Backup Configuration`
  * Works as expected  
  * Creating, Restoring, Comparing and Managing backups is straight forward  
  * Fetch config needed after any configuration change?
  * After adding device it remains on device details... should go to inventory list.

## F5 Big-IP System  
  
* `Golden Config Compliance`  
  * Works as expected
  * Needs documentation and examples for non-default remediation commands

* `F5 BIG-IP CVE_Reporting`
  * Works as expected
  * Needs copy/paste/link function of CVE URL field
  * Needs description of CVE in report not just the CVE number

* `Fetch_F5 BIG-IP CVEs`
  * Works as expected
  * How often? Should this be automatically scheduled?
  *	Slow process. How bigis the file? Does it pull entire DB each time or just the deltas?

* `Software Upgrades`
  * If there is not enough HDD it still creates volume.
  * Needs workflow to remove inactive volumes?
  * Works as expected
  * Allows upgrade to 17.x but then can't manage that version - FYI
  * Needs workflow to manage images on devices. /shared/images
  * Upgraded to v16 - Holds @ Object Count to proceed - Needs a /y option here?
  * Held at license check… in spite of set to auto
  * After failure it leaves device off-line. By design? Option?
  * Cannot use existing volume only create new one?
  * This means a failed install has orphaned volumes
  * After upgrade had to fetch config? Wasn't available for other workflows until updated (fetched)
  * e.g. Enable pool member

## F5 Big-IP LTM

* `Create Advanced VIP`
  * Create A record should have BigIP as a Vendor (i.e. WideIP option)
  * Why does it flip fields on redirect check box?
  * Workflow hung while loading keys. (create new)
  * Would not take 4-part FQDN (e.g. avx.wideip.domain.com) as FQDN only 3-part

* `Disable and Delete Unused VIP`
  * Workflow Empty - Failed/Success

* `Disable Pool Member`
  * Why must I select a VS? Some pools exist in multiple VS or not at all e.g. iRule selected pools
  * Only see VIPs in Common partition - Tested this multiple times
  * Logic and usability is flawed.  Add button? /update. Kludgy
  * Saw various errors on multiple tests
    * Prevalidation Failed - Device memory exceeded threshold
    * java.util.ArrayList error & others (seems buggy)


## F5 Big-IP AS3

* `Create App Service`
  * Worked as expected with limited flexibility
  * Needs ability to import/create custom AS3/FAST Templates

* `Modify LTM Service`
  * To modify a service you need the details so why the extra step(s)? Get Virtuals Get Pools
  * Unable to select pool until you Get VS
  * No bulk edit - e.g. port change on multiple pool members
  * Allows the entry of duplicate pool members but fails after submission - Needs entry error checking
  * Additional details (SNAT, Monitor, etc.) all reset to none when modifying forcing re-selection

* `Fetch App Services`
  * Should be allowed to pull all (or selected) AS3 partitions
  * This workflow simply dumps the json into the page. What's the value here?

* `Delete Application Services`
  * Doesn't see all apps - One device it didn't see any of three AS3 apps
  * Doesn't remove partition
  * Too many steps to pull info from the device (get vs, get pools, etc.)

## F5 Big-IP GTM

* `Modify GTM WideIP`
  * Did not work as expected
  * Pool member change not relected after successful submission
  * Too many steps to make a simple change IMHO

## Other Notes

* Pool members in certain lists have to be hovered to see. /partition/device/partition/etc... doesn't fit
* Adding memebers to pools resets back to generic host... tedious
* Need DC/Device filter for selecting pool members
* WideIP doens't allow for selecting existing GSLB pool





