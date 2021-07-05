# Security Overview

Cirrent takes product and network security very seriously. Every aspect of the Cirrent service has been designed with security in mind – protecting the connected products and protecting the Cirrent cloud,

## Securing the Device Credentials

Every device is pre-provisioned during manufacturing with a unique device identifier and a device secret (the device credentials). It is up to the product company to determine how best to protect these credentials on the device, and Cirrent works closely with the product companies to ensure that best practices are being followed to protection these credentials. As each device has a unique set of credentials, exposure of one set of credentials is a limited risk, as they cannot be used to gain access to information for any other device.

The device secret is used to derive the  **API key**. When the device has an Internet connection, it makes calls to the Cirrent cloud. All device to cloud communication is over HTTPS. The device uses the device id and the  **API key**  to authenticate to the Cirrent cloud, and validates that the certificate being presented matches the Cirrent cloud certificate that is pre-configured in the device.

## Securing Cirrent’s Cloud

The Cirrent cloud is deployed as a geographically redundant set of servers within the Amazon Web Services. Cirrent follows the AWS recommendations to ensure that the Cirrent cloud is scalable, robust and secure. The Cirrent cloud is regularly audited to ensure that it conforms to industry best practices for secure cloud services.

## Engineering best practices

All the software that Cirrent develops is intended for production use, and conforms to industry best practice for production software. For example, any passwords entered in any Cirrent software are never written to a log file. The software does not contain any debug backdoors or ways to enable unauthorized access.
