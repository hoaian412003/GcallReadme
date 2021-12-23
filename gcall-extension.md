# GCALLS PLUS 

***

Gcalls 3.1 webphone is an web extension. Click to call any contacts inside various CRM platforms. Synchronize data inside Gcalls Webphone and Gcalls Plus systems.

### Deployment
***
* Update latest version in manifest file
* Check env to make sure Environment variable is production 
* Login Developer dashboad (chrome web store) to deploy with account developer.gpat@gmail.com

### Development

***
##### Add a new domain
you have to add new domain to the following files:
* __manifest.json__
* variable tab_urls in __background.js__
* variable tab_urls in __popup/account.js__
##### Integration
* Refer to the following cases according to your CRM integration requirements:
    * __Click-to-call__ : sogo, netvieclam, CRM (those need only click-to-call) or any CRM 
    * __custom iframe__: hubspot, mio, pipdrive, zendesk, bitrix
    * __Click-to-call with general format__: viecco, antoree, btaskee
    *  __html iframe__: btaskee
    * __Click-to-call with hidden phone__: viecco, xsales
    *  __sms__: hubspot, mysapogo, vinacapital, bitrix24, zendesk
* Notes:
    * file callbox.js is always needed all cases integration
    * Be careful when adding a new permission in manifest. If you add redundant permissions, you will be rejected that version (In that case, if you already have a published version of this item on the Chrome Web Store, it has not been affected and is still available.)
    * **Important Note**:
    Repeated or egregious policy violations in the Chrome Web Store may result in your developer account being suspended or could lead to a ban from using the Chrome Web Store platform.