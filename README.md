# anypoint-datablind-policy
Artifacts required for using Data Blind as a Gateway Policy in Anypoint API Manager.

## How to Publish this policy to your Exchange

1. Clone this repo
```
       git clone https://github.com/mjegann5/anypoint-datablind-policy.git
```
2. In pom.xml replace ANYPOINT_ORG_ID to your Anypoint Org Id
```
       <groupId>ANYPOINT_ORG_ID</groupId> => <groupId>5tdfgceb5-fd1f-456d-aaa2-19cdsddcea</groupId>
```
3. Run the maven command to deploy data blind to your exchange. (anypoint_username and anypoint_password are your anypoint platform credentials)

```
       mvn deploy -DskipTests -s .\settings.xml -Danypoint_username="******" -Danypoint_password="******" -Dcwrepo_username="Token" -Dcwrepo_password="******************"


       
```
