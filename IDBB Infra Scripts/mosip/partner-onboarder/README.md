# Partner Onboarder

## Overview
Loads certs for default partners for sandbox. Refer [mosip-onboarding repo](https://github.com/tf-govstack/mosip-onboarding).

## Install 
* Set `values.yaml` to run onboarder for specific modules.
* run `./install.sh`.
```
./install.sh
```
### Configurational steps after onboarding is completed.
* Onboarding the default mimoto-keybinding partner using below mentioned steps.
* After successfull partner onboarder run, html report containing detailed request and response bodies are saved inside `onboarder` bucket in minio.
* Get `apiKey` from  response body of  request `request-for-partner-apikey` from the report **_mimoto-keybinding.html_**.
* Update & commit  value of  `wallet.binding.partner.api.key`  parameter with `apiKey` value from last step in **mimoto-default.properties**.
* Restart mimoto pod.
# Troubleshootings

* After completion of the job, a very detailed `html report` is prepared and stored at https://onboarder.{sandbox_base_url}.mosip.net

* The user can go and view the same for more information or response messages.

### Commonly found issues 

 1. KER-ATH-401: Authentication Failed
 
    Resolution: You need to provide correct secretkey for mosip-deployment-client.
 
 2. Certificate dates are not valid

    Resolution: Check with admin regarding adding grace period in configuration.
 
 3. Upload of certificate will not be allowed to update other domain certificate
 
    Resolution: This is expected when you try to upload `ida-cred` certificate twice. It should only run once and if you see this error while uploading a second      time it can be ignored as the cert is already present.



