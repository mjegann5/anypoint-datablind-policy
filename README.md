# anypoint-datablind-policy
Artifacts required for using Data Blind as a Gateway Policy in Anypoint API Manager.

## API Response without DataBlind Policy

```
{
	    "legal" : 
 		[   
 			{ 
 			"firstName" : "John",  
 			"lastName"  : "Doe",
 			"age"       : 23 
 			},
			{
			"firstName" : "Mary",  
 			"lastName"  : "Smith",
 			"age"      : 32 
 			}
 		],                           
	    "marketing": 
		[ 
  			{ 
  			"firstName" : "Sally",
  			"lastName"  : "Green",
  			"age"      : 27 
 			}, 
  			{ 
  			"firstName" : "Jim", 
  			"lastName"  : "Galley",
  			"age"       : 41 
  			}
  		],
  	    "companyName" : "True Value Corporation",
  	    "address" : "123 First Street, Newyork, NY, USA",
  	    "contactNumber" : "123456789"
}
 ```

## API Response with DataBlind Policy
```
{
    "legal": [
        {
            "firstName": "ooQ9OqV3wIZeG+MkEk1KFw==",
            "lastName": "Ees",
            "age": "#######################"
        },
        {
            "firstName": "/bbIa8Bzy76zsfqnUKWt7A==",
            "lastName": "Edmgy",
            "age": "#######################"
        }
    ],
    "marketing": [
        {
            "firstName": "Sally",
            "lastName": "Green",
            "age": 27
        },
        {
            "firstName": "Jim",
            "lastName": "Galley",
            "age": 41
        }
    ],
    "companyName": "True Value  Corporation",
    "address": "123 First Street, Newyork, NY, USA",
    "contactNumber": "128388658"
}
```

# How to apply DataBlind to your API

## Publish Datablind Assets to your exchange 

1. Publish Datablind Connector to your exchange.
   Follow the instructions at https://github.com/mjegann5/anypoint-data-blind-connector
   
2. Publish Datablind Policy to your exchange
- 2.1 Clone this repo
```
       git clone https://github.com/mjegann5/anypoint-datablind-policy.git
```
- 2.2 In pom.xml replace ANYPOINT_ORG_ID by your Anypoint Org Id
```
       <groupId>ANYPOINT_ORG_ID</groupId> => <groupId>5tdfgceb5-fd1f-456d-aaa2-19cdsddcea</groupId>
```
- 2.3 Run the maven command to deploy datablind policy to your exchange. (anypoint_username and anypoint_password are your anypoint platform credentials. Contact mjegann@kavisoft.net to get a valid cwrepo_password.)
```
	mvn deploy -DskipTests -s .\settings.xml -Dmuleentrepo_username="******" -Dmuleentrepo_password="******" -Danypoint_username="******" -Danypoint_password="******" -Dcwrepo_username="Token" -Dcwrepo_password="******************"
```
## Configure Policy in API Manager

1. Policy parameters
   
| Parameter | Description | Required | Example |
| --------- | ----------- | -------- | ------- |
| Datablind Key | Encryption Key used by the DataBlind | Required  | #["1234567812345678"] |
| Manually Specify Sensitive Fields | Select if you want to manually specify the sensitive fields in the API response | Required  | Click to Select |
| Sentitive Fields | Sensitive fields in the API response | Required  | #[{    "Title" : "FE:PersonName"  }] |
| Eligible HTTP Codes | Apply Datablind only when the API response has the following HTTP Codes | Required  | #["200,201,202,205,213"] |
| Override Token for DataBlind | When a valid override token is provided, Datablind returns the unencrypted and unmasked data | Optional  | #[attributes.headers['dataBlindToken']] |
| Passphrase used when creating the Override Token for DataBlind | When a valid override token passphrase is provided, Datablind returns the unencrypted and unmasked data  | Optional  | #[attributes.headers['dataBlindPassphrase']] |

   
2. Example Policy Configuration

   ![Concept](/assets/DataBlind-Policy.JPG)
