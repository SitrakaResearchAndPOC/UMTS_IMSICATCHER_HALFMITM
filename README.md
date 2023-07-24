# GSM5_UMTS_IMSICATCHER_HALFMITM
## Reading articles
* [layakk](https://www.layakk.com/en/research/) [rootedcon2016](https://github.com/SitrakaResearchAndPOC/GSM5_UMTS_IMSICATCHER_HALFMITM/blob/main/Hackron2016-Layakk-3G_Attacks.pdf) [rootedcon2016_v2](https://github.com/SitrakaResearchAndPOC/GSM5_UMTS_IMSICATCHER_HALFMITM/blob/main/Layakk-RC16-FINALv2%20(2).pdf)
* fakebts3g [pdf](https://github.com/SitrakaResearchAndPOC/GSM5_UMTS_IMSICATCHER_HALFMITM/blob/main/fakebts3g.pdf) [link](https://fakebts.com/category/3g/)
* fakebts3g_v2 [pdf](https://github.com/SitrakaResearchAndPOC/GSM5_UMTS_IMSICATCHER_HALFMITM/blob/main/imsicatching-attacks-on-3g-networks-part-1.pdf)  [link](https://fakebts.com/2017/10/imsicatching-attacks-on-3g-networks-part-1/)
* [videos1](https://www.youtube.com/watch?v=KM_ErNK3x04&t=1912s) [videos2](https://www.youtube.com/watch?v=32DD5DSAnc8&t=86s)
* Protocol 3G in 28C3 [videos3](https://www.youtube.com/watch?v=4wF47aLagoU&pp=ygUTaGFyYWxkIHdlbHRlICsgdW10cw%3D%3D)
  
## SIMPLE IMSI CATCHER
### Attack explanation
* Just catch IMSI
* Finding all parameter1 (using android apps) MCC, MNC, RAU1 and UARFCN1 as same as operator like NodeB_Jammer
* Options 1 : launch NodeB_Jammer openbts_umts as parameter1
* Options 2 : launch NodeB_Jammer using Modmobmap or CleverJam with same frequency as UARCN1 and bandwith 5MHz 
* Finding all parameter2 (using android apps) MCC, MNC, RAU2 and UARFCN2 as same as operator like NodeB_Collector
* Stop NodeB_Jammer
* launch NodeB_Collector as same as MCC, MNC, RAU3 different of RAU2 and UARFCN2
* launch NodeB_Jammer as same as options1 or options2
* Collect IMSI

 ### Protocol Flow 
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing1.jpg">
</p>


## UMTS DENIED OF SERVICE
### Attack explanation
* Sending Location Update Reject for making Denied of service having code number 3 "Illegal MS"
### Protocol Flow 
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing2.jpg">
</p>
 ### Reject Code list
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing3.jpg">
</p>



## IMSICATCHING ATTACKS ON 3G NETWORKS (Bidding Down Attack)
* For bidding down attack (bda2g) uses Location Update Reject having code number 14 "Service option temporarily out of order"
### Descriptions
In June of this year I announced the participation of CellAnalysis in the project of Sysmocom [Accelerate3g](https://www.sysmocom.de/news/contribute-to-3g5-acceleration/index.html) [videos1](https://www.youtube.com/watch?v=vq4zXOk3Qpg&pp=ygUTaGFyYWxkIHdlbHRlICsgdW10cw%3D%3D)  [videos2](https://www.youtube.com/watch?v=ol27YxWOcuY&pp=ygUTaGFyYWxkIHdlbHRlICsgdW10cw%3D%3D) program to detect the 3G IMSICatching attacks. This article describes the first steps studying the 3G attacks within the Osmocom infrastructure and the basic principles of detection that are being implemented in CellAnalysis 3G.

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


## UMTS REDIRECTOR
### Attack explanation
* Make a denied of service with redirectioncarrier info attack [code]()
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
 

## CRYPTO HACKING USING RAINBOW TABLE
* Create a rainbow table for cracking crypto openbts-umts [code](https://github.com/SitrakaResearchAndPOC/fork_a53_rainbow_wip)


## UMTS CBC(CELL BROADCAST CENTER)
* Sending a fake panic attack (fake notification, emergency sms)

## Remark
* Choose the best parameter of [UHD](https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/UHD_openbts_umts.jpg) for openbts_umts
* No opensource for umts client , so no full mitm opensource
* Femtocell3G for osmocom named osmo-iuh (more expensive)
