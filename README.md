# anypoint-datablind-policy
Artifacts required for using Data Blind as a Gateway Policy in Anypoint API Manager.

## How to Publish this policy to your Exchange

1. Clone this repo
```
       git clone https://github.com/mjegann5/anypoint-datablind-policy.git
```
2. In pom.xml replace ANYPOINT_ORG_ID by your Anypoint Org Id
```
       <groupId>ANYPOINT_ORG_ID</groupId> => <groupId>5tdfgceb5-fd1f-456d-aaa2-19cdsddcea</groupId>
```
3. Run the maven command to deploy datablind policy to your exchange. (anypoint_username and anypoint_password are your anypoint platform credentials. Contact mjegann@kavisoft.net to get a valid cwrepo_password.)

```
       mvn deploy -DskipTests -s .\settings.xml -Danypoint_username="******" -Danypoint_password="******" -Dcwrepo_username="Token" -Dcwrepo_password="******************"


       
```
5. Policy Parameters

| Parameter | #Description  | #Required  | #Example |
| ------- | --- | --- |
| Manually Specify Sensitive Fields | Select if you want to manually specify the sensitive fields in the API response | Required  | Click to Select |
| Sentitive Fields | Sensitive fields in the API response | Required  | #[{    "Title" : "FE:PersonName"  }] |
| Eligible HTTP Codes | Apply Datablind only when the API response has the following HTTP Codes | Required  | #["200,201,202,205,213"] |
| Override Token for DataBlind | When a valid override token is provided, Datablind returns the unencrypted and unmasked data | #[attributes.headers['dataBlindToken']] | Required  |
| Passphrase used when creating the Override Token for DataBlind
| When a valid override token passphrase is provided, Datablind returns the unencrypted and unmasked data  | Required  | #[attributes.headers['dataBlindPassphrase']] |



   
4. Example Policy Configuration

   ![Concept](/assets/DataBlind-Policy.JPG)
