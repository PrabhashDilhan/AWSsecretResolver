# AWSsecretResolver

## This class mediator can be used to resolve AWS secrets in the WSO2 EI mediation flow.


### Steps to appy the class mediator

1. build maven project and copy the bundle jar file to the <EI_HOME>/dropins direcotry.
2. Start the server and you can use below service to test class mediator.

*SAMPLE SERVICE*

```
<?xml version="1.0" encoding="UTF-8"?>
<proxy xmlns="http://ws.apache.org/ns/synapse"
       name="test"
       transports="http https"
       startOnLoad="true">
   <description/>
   <target>
      <inSequence>
         <class name="org.wso2.aws.SecretResolverAWS">
            <property name="secretName" value="test/my"/>
            <property name="region" value="us-east-1"/>
            <property name="accessKey" value="your aws accessKey"/>
            <property name="secretKey" value="your aws secretKey"/>
         </class>
         <payloadFactory media-type="text">
            <format>$1</format>
            <args>
               <arg evaluator="xml" expression="get-property('test/my')"/>
            </args>
         </payloadFactory>
         <respond/>
      </inSequence>
   </target>
</proxy>
```
