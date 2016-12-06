# [![**Brooklyn**](https://brooklyn.apache.org/style/img/apache-brooklyn-logo-244px-wide.png)](http://brooklyn.apache.org/)

### Trans-cloud Samples

This module contains some trans-cloud application samples.

##Deployng applications

Trans-cloud Brooklyn contains [brooklyn-tosca plugin](https://github.com/cloudsoft/brooklyn-tosca/)
so trans-cloud applications can be modeled following the [TOSCA yaml profile]
(http://docs.oasis-open.org/tosca/TOSCA-Simple-Profile-YAML/v1.0/csprd01/TOSCA-Simple-Profile-YAML-v1.0-csprd01.html) specification.

Applications can be deployed using the Brooklyn Web Console. Visit Brooklyn documentation to learn about
[BluePrint deployments](https://brooklyn.apache.org/v/latest/start/blueprints.html).

##Examples
Here you have some sample application TOSCA templates.
* [Softcare](https://github.com/kiuby88/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/softcare.yaml)
* [WebChat](...)(Soon)

These examples specify a generic location (`<LOCATION>`) for each application module. `<LOCATION>`
can be replaced by any location available in Brookly, [here](https://brooklyn.apache.org/v/latest/yaml/setting-locations.html)
you can find information about the supported Brooklyn providers and how they can be specified in a blueprint.

For example, the following code contains a location policy description that adds a provider location
to the `Softcare_dashboard` module of the [Softcare](https://github.com/kiuby88/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/README.md) application.

    add_Softcare_dashboard_locations:
      members: [ Softcare_dashboard ]
      policies:
      - brooklyn.location: <LOCATION>

The `<LOCATION>` slot can be replaced by any location available in Brookly. For example, Pivotal Web Services:

    add_Softcare_dashboard_locations:
      members: [ Softcare_dashboard ]
      policies:
      - brooklyn.location:
          cloudfoundry:
            user: <AKA_YOUR_USER_EMAIL>
            password <password>
            org: <organization>
            endpoint: <API_endpoint>
            space: <space>
            address: <platform_address>

For Amazon EC2 Oregon:

    add_Softcare_dashboard_locations:
      members: [ Softcare_dashboard ]
      policies:
      - brooklyn.location:
          jclouds:aws-ec2:
            region: <us-west-2>
            identity: <user-key-id>
            credential: <user-key>


These are some sample applications with preconfigured locations:

* [Softcare on AWS Oregon, Softlayer Seattle and Pivotal](https://github.com/kiuby88/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/softcare_aws_softlayer_pivotal.yaml)
* [Softcare on AWS Oregon, AWS Ireland and Pivotal](https://github.com/kiuby88/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/softcare_aws_pivotal.yaml)
* [Softcare on AWS and Bluemix](https://github.com/kiuby88/brooklyn-dist/blob/trans-cloud/trans-cloud-samples/softcare_aws_bluemix.yaml)
* [WebChat on AWS and Pivotal](...) (Soon)

The locations can be specified using a simple string, for example `aws-ec2:us-west-2` for AWS Oregon,
or `pivotal-instance` for Pivotal, but this requires [Brookly properties configuration](https://brooklyn.apache.org/v/latest/ops/locations/).

