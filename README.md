# AWSsecretResolver

## This class mediator can be used to resolve AWS secrets in the mediation flow.

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
