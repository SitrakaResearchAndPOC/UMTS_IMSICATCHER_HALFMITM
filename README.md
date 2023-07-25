# UMTS_IMSICATCHER_HALFMITM
## Reading articles
* [layakk](https://www.layakk.com/en/research/) [rootedcon2016](https://github.com/SitrakaResearchAndPOC/GSM5_UMTS_IMSICATCHER_HALFMITM/blob/main/Hackron2016-Layakk-3G_Attacks.pdf) [rootedcon2016_v2](https://github.com/SitrakaResearchAndPOC/GSM5_UMTS_IMSICATCHER_HALFMITM/blob/main/Layakk-RC16-FINALv2%20(2).pdf)
* fakebts3g [pdf](https://github.com/SitrakaResearchAndPOC/GSM5_UMTS_IMSICATCHER_HALFMITM/blob/main/fakebts3g.pdf) [link](https://fakebts.com/category/3g/)
* fakebts3g_v2 [pdf](https://github.com/SitrakaResearchAndPOC/GSM5_UMTS_IMSICATCHER_HALFMITM/blob/main/imsicatching-attacks-on-3g-networks-part-1.pdf)  [link](https://fakebts.com/2017/10/imsicatching-attacks-on-3g-networks-part-1/)
* [videos1](https://www.youtube.com/watch?v=KM_ErNK3x04&t=1912s) [videos2](https://www.youtube.com/watch?v=32DD5DSAnc8&t=86s)
* Protocol 3G in 28C3 [videos3](https://berlin-ak.ftp.media.ccc.de/congress/2011/webm/28c3-4663-en-cellular_protocol_stacks_for_internet.webm) [videos4](https://www.youtube.com/watch?v=4wF47aLagoU&pp=ygUTaGFyYWxkIHdlbHRlICsgdW10cw%3D%3D)
* Location Update Reject or LUR [pdf](https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/cause-codes-umts-lte-3gpp.pdf) [link](http://prerak.com/tag/cause-codes-umts-lte-3gpp/)

## New AKA security (Mutual authentication)
* [link1](https://www.3glteinfo.com/lte-security-architecture/) [link2](https://www.tech-invite.com/3m33/toc/tinv-3gpp-33-102_d.html)

* Simpilied AKA
<p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/UMTS-authentication-and-key-agreement.png">
</p>

* Detailed AKA
<p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/UMTS-AKA-Authentication-Protocol.png">
</p>


## LIST OF ATTACK
*  SIMPLE IMSI CATCHER
*  UMTS DENIED OF SERVICE
*  JAMMING
*  BIDDING DOWN ATTACK
*  UMTS REDIRECTOR
*  CRYPTO HACKING USING RAINBOW TABLE
*  FEMTOCELL_HACKING
*  UMTS CBC(CELL BROADCAST CENTER)

## 1. SIMPLE IMSI CATCHER
### Attack explanation
* Just catch IMSI
* Finding all parameter1 (using android apps) MCC, MNC, RAU1 and UARFCN1 as same as operator like NodeB_Jammer
* Options 1 : launch NodeB_Jammer openbts_umts as parameter1
* Options 2 : launch NodeB_Jammer using Modmobmap or CleverJam with same frequency as UARCN1 and bandwith 5MHz 
* Finding all parameter2 (using android apps) MCC, MNC, RAU2 and UARFCN2 as same as operator like NodeB_Collector
* Stop NodeB_Jammer
* launch NodeB_Collector as same as MCC, MNC, RAU3 different of RAU2 and UARFCN2 and location update reject with code 15 (No Suitable cells in area)
* launch NodeB_Jammer as same as options1 or options2
* Collect IMSI

 ### Protocol Flow 
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing1.jpg">
</p>


## 2. UMTS DENIED OF SERVICE
### Attack explanation
* Sending Location Update Reject for making Denied of service having code number 3 "Illegal MS"
### Protocol Flow 
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing2.jpg">
</p>
 ### Reject Code list
 <p align="center">
  <img width="600" height="250" src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing3.jpg">
</p>



## 3. IMSICATCHING ATTACKS ON 3G NETWORKS (Bidding Down Attack)
* For bidding down attack (bda2g) uses Location Update Reject having code number 14 "Service option temporarily out of order"
### Descriptions
In June of this year I announced the participation of CellAnalysis in the project of Sysmocom [Accelerate3g](https://www.sysmocom.de/news/contribute-to-3g5-acceleration/index.html) [videos1](https://www.youtube.com/watch?v=vq4zXOk3Qpg&pp=ygUTaGFyYWxkIHdlbHRlICsgdW10cw%3D%3D)  [videos2](https://www.youtube.com/watch?v=ol27YxWOcuY&pp=ygUTaGFyYWxkIHdlbHRlICsgdW10cw%3D%3D) [videos3](https://www.youtube.com/watch?v=oQU10iSvW-4&pp=ygUgUnVubmluZyB5b3VyIG93biAzRy8zLjVHIG5ldHdvcms%3D) [videos4](https://www.youtube.com/watch?v=PQ1koemaLf0&pp=ygUgUnVubmluZyB5b3VyIG93biAzRy8zLjVHIG5ldHdvcms%3D) [videos5](https://www.youtube.com/watch?v=PQ1koemaLf0&pp=ygUmQ3JlYXRpbmcgR1NNIE5ldHdvcmsgKyBzeWx2YWludCBtaW5hdXQ%3D) program to detect the 3G IMSICatching attacks. This article describes the first steps studying the 3G attacks within the Osmocom infrastructure and the basic principles of detection that are being implemented in CellAnalysis 3G.

### Lab infrastructure
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/diagrama2.png">
</p>

Following the steps in the [Getting_Started_with_3G](https://osmocom.org/projects/cellular-infrastructure/wiki/Getting_Started_with_3G) tutorial,  we setup the 3G network but we will modify the MSC node source code. We don’t need to add any subscriber in the HLR/AuC database, since we are not going to deliver a 3G service to our victims. The negotiation procedure of the mobile to register in our 3G network will always be rejected, in order to be able to downgrade to 2G, in the same way as we saw in 4G ([4G/LTE IMSI Catchers](https://fakebts.com/%202017/04)). In this first article we will use the “Location Update Reject” attack, with the different causes of rejection forcing the mobile to register in the 2G network (the downgrade attack).

### Implementation
3G
<br/>
femtocell nano3G (Sysmocom)
<br/>
Osmocom 3G network,  running on Ubuntu 14 (intel core i5 4200U 1,6GHz, 8Gb RAM)
<br/>
<br/>

2G
<br/>
BladeRF x40
<br/>
YateBTS, 2G network running on Ubuntu 16 (intel atom 1.6GHz, 8GB RAM)
<br/>
<br/>
Once configured the 3G network following the Getting Started tutorial, it’s better to verify that the cell 3G is transmitting correctly in the UARFCN 9800 (default channel):
<p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/RFAnalyzer.png">
</p>

To implement our custom reject cause, we must modify the source code of the MSC to overwrite the registration reject cause in the “Location Update Request” response. Usually the reject cause should be “(2) IMSI unknown in HLR” since we have not provisioned any subscriber in our HLR or “(3) Illegal MS” if we only add the victim’s IMSI in the HLR Sqlite db but not the auth values. It’s needed to manipulate the source code of the MSC so that it always returns the cause value of our interest, according to whether we want to do a D.o.S or a 2G downgrade attack:
<br/>
* Disable the USIM entirely until power-off or USIM removal.
* Attach requests disable the USIM for packets domain until power-off or USIM removal.
* Periodic Location Update requests will trigger the UE to attempt GERAN instead.
Once we choose and implement our attack, switch-on the victim mobile (S2) and activate Tobias Engel xgoldmon to detect the attack. Check the following image, how the response to the registration request (the Location Update Reject) is correctly sent to our victim with our reject cause choosen (this example is #14, “Service option temporarily out of order“):
<p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/LocUpRjt14_xgoldmon.png">
</p>

After the LocUp Reject, the victim mobile connects to the 2G network (YateBTS). See bellow how after the RRC message “Location Update Reject“, the mobile starts to use LAPDm and begins the authentication in the 2G network:

<p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/Downgrade_2G_xgoldmon.png">
</p>

But, before switching to 2G network, the registration procedure has asked the victim mobile to identify, by requesting the IMSI. This is the 3G IMSICatching attack, see the “Identity Response” message (IMSI has been removed in the image):

<p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/Downgrade_2G_xgoldmon.png">
</p>

#### Detection
CellAnalysis 3G uses active monitoring solutions (in this article xgoldmon), instead of the passive ones as SDR boards used in the 2G fake stations detection, to monitor 3G attacks.
<br/>
Advantages using active monitoring;
<br/>
ciphering algorithms (UEA) usage
<br/>
authentication parameters and rates
<br/>
But on the other hand, there is a big disadvantage:
<br/>
<br/>
one SIM card and device per operator in order to scan all the 3G fake stations
<br/>
Of course a regulation compliance check is being carried out to determine wether the 3G radio parameters are used accordingly to each country frequency distribution regulation, as in the 2G detection.


### Important Comments
Yes, there is a periodic location update timer in both 2G (osmo-bsc) and 3G (osmo-msc):
<br/>
osmobsc-vty-reference.pdf: “1.15.45 periodic location update <6-1530>”
<br/>
osmomsc-vty-reference.pdf: “1.14.9 periodic location update <6-1530>”

## 4. UMTS REDIRECTOR
### Attack explanation
* Make a denied of service with redirectioncarrier info attack [code](https://github.com/SitrakaResearchAndPOC/umts_redirection)
 ### Protocol Flow 
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing4.jpg">
</p>

 ### Attack scenario global
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing5.jpg">
</p>

 ### Attack scenario 1 : the mobile connects to the 3G
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing6.jpg">
</p>

### Attack scenario 2 : the fake bts sends redirected carrier info
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing7.jpg">
</p>

### Attack scenario 2 : the victim is at the fake 2G network
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing8.jpg">
</p>

## 5. CRYPTO HACKING USING RAINBOW TABLE
* Create a rainbow table for cracking crypto openbts-umts [code](https://github.com/SitrakaResearchAndPOC/fork_a53_rainbow_wip)

## 6. FEMTO_CELL HACKING
* Rooted the femtocell for having a mitm
* Could hack SS7
  
## 7. UMTS CBC(CELL BROADCAST CENTER)
* Sending a fake panic attack (fake notification, emergency sms)

## Remark
* Choose the best parameter of [UHD](https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/UHD_openbts_umts.jpg) for openbts_umts
* No opensource for umts client , so no full mitm opensource
* Femtocell3G for osmocom named osmo-iuh (more expensive)
