C:\terraform\aries-terraform-aep\aries-terraform-aep\environments\dev>aws route53 list-hosted-zones --profile aep-aries --query "HostedZones[].[Name,Id,Config.PrivateZone]" --output table
-------------------------------------------------------------------------------------------------
|                                        ListHostedZones                                        |
+------------------------------------------------+-------------------------------------+--------+
|  rosa.mas-sbx2.tcu7.p3.openshiftapps.com.      |  /hostedzone/Z06009582M2EF505MOY5F  |  False |
|  sandbox-gb.cloud.aep.com.                     |  /hostedzone/Z0736140Z7D8RSOM226G   |  False |
|  cloud.aep.com.                                |  /hostedzone/Z07331021PJL72XPRQ45K  |  False |
|  eeg.cloud.aep.com.                            |  /hostedzone/Z05251923PJ65OTH43362  |  False |
|  rosa.mas-midw-sbx1.taom.p3.openshiftapps.com. |  /hostedzone/Z10391192XBTKLY82VLQV  |  False |
|  rosa.mas-rxs-sbx1.5ud2.p3.openshiftapps.com.  |  /hostedzone/Z01290443GKIS0UJB13K5  |  False |
|  rosa.mas-sbx2.tcu7.p3.openshiftapps.com.      |  /hostedzone/Z10007212AFM2FSFASU77  |  True  |
|  mas-midw-sbx1.hypershift.local.               |  /hostedzone/Z08153062QDSK4BEOJGJU  |  True  |
|  rosa.mas-midw-sbx1.taom.p3.openshiftapps.com. |  /hostedzone/Z080301128MRSR5Q5J52I  |  True  |
|  mas-sbx2.hypershift.local.                    |  /hostedzone/Z00841631QV333BI1W2F1  |  True  |
|  glue.us-east-1.amazonaws.com.                 |  /hostedzone/Z09047751KM2SGXZ6KXMP  |  True  |
|  mas-rxs-sbx1.hypershift.local.                |  /hostedzone/Z0789333IWM5BF9IJ3Y2   |  True  |
|  rosa.mas-rxs-sbx1.5ud2.p3.openshiftapps.com.  |  /hostedzone/Z07883762NEQGU9D1E9Q   |  True  |
|  s3.us-east-1.amazonaws.com.                   |  /hostedzone/Z05135851CWDARCQF90PX  |  True  |
+------------------------------------------------+-------------------------------------+--------+


C:\terraform\aries-terraform-aep\aries-terr
