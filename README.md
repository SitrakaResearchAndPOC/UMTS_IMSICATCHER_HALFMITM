# GSM5_UMTS_IMSICATCHER_HALFMITM
## Reading articles
* [layakk](https://www.layakk.com/en/research/) [rootedcon2016](https://github.com/SitrakaResearchAndPOC/GSM5_UMTS_IMSICATCHER_HALFMITM/blob/main/Hackron2016-Layakk-3G_Attacks.pdf) [rootedcon2016_v2](https://github.com/SitrakaResearchAndPOC/GSM5_UMTS_IMSICATCHER_HALFMITM/blob/main/Layakk-RC16-FINALv2%20(2).pdf)
* fakebts3g [pdf](https://github.com/SitrakaResearchAndPOC/GSM5_UMTS_IMSICATCHER_HALFMITM/blob/main/fakebts3g.pdf) [link](https://fakebts.com/category/3g/)
* fakebts3g_v2 [pdf](https://github.com/SitrakaResearchAndPOC/GSM5_UMTS_IMSICATCHER_HALFMITM/blob/main/imsicatching-attacks-on-3g-networks-part-1.pdf)  [link](https://fakebts.com/2017/10/imsicatching-attacks-on-3g-networks-part-1/)
* [videos1](https://www.youtube.com/watch?v=KM_ErNK3x04&t=1912s) [videos2](https://www.youtube.com/watch?v=32DD5DSAnc8&t=86s)

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
* For bidding down attack (bda2g) uses having code number 14 "Service option temporarily out of order"
 ### Protocol Flow 
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing2.jpg">
</p>
 ### Reject Code list
 <p align="center">
  <img src="https://github.com/SitrakaResearchAndPOC/UMTS_IMSICATCHER_HALFMITM/blob/main/umts_flow_imsi_cathing3.jpg">
</p>

## UMTS REDIRECTOR
### Attack explanation
* Make a denied of service with redirectioncarrier info attack
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
