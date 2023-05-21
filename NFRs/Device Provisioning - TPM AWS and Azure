When designing IoT platforms, a crucial aspect is device provisioning or registration also known as device onboarding. In this blog post, I will discuss device provisioning in general and explore the options available on Azure and AWS cloud platforms, focusing on state-of-the-art techniques.

The simplest approach to device provisioning involves manual device registration in AWS using the AWS Console or AWS CLI, and in Azure, using the Azure portal or Azure CLI. This method is commonly adopted by most teams, particularly in R&D/Engineering. However, for production purposes, this approach is not feasible to meet all the non-functional requirements (NFRs) of DPS (Device Provisioning Service).

The common NFRs for DPS include:

1. Security of device identity and mutual authentication with service endpoints.
    
2. Security of the end-to-end provisioning process.
    
3. Integration with high-volume manufacturing.
    
4. Integration with contract manufacturing.
    
5. Ease of installation and commissioning of devices.
    
6. Bulk onboarding of devices.
    
7. Ownership transfers.
    
8. Re-provisioning of devices.
    
9. Device hardware replacement.
    
10. Device certificate rotation.
    
11. Support for multi-tenancy.
    
12. Load balancing.
    
13. Geo-sharding of devices.
    

In order for an IoT device to connect and communicate with service endpoints or other device endpoints, it is necessary to establish trust with those endpoints. This trust is established through mutual authentication between the device and the endpoints, using security principals. Whether the endpoints belong to AWS IoT Core or Azure IoT Hub, the device must have the following security principals.

1. **Device Key Pairs**: Each device has a unique set of private and public key pairs. It's important to securely store the private key, and TPM chips are the state-of-the-art technology to secure private keys.
    
2. **X.509 Device Certificate**: The device must have a certificate signed by a Certificate Authority (CA). The service side should possess the appropriate CA Certificate to validate the device's certificate.
    
3. **Service Endpoints**: AWS and Azure provide service endpoints for device communication.
    
4. **Signing CA Certificate**: The CA certificate is used to sign the X.509 device certificate.
    
5. **Service Root CA Certificate**: This certificate verifies the authenticity of the service endpoints, allowing the device to trust the endpoints it communicates with.
    

When designing an IoT platform, it is crucial to carefully consider the installation, activation, and generation of cryptographic key material and certificates on IoT devices. The architecture must ensure both the security and scalability of the installation and commissioning process.

One of the key factors which influence the design of this architecture is the end-to-end device supply chain.

Broadly, the options to add the Principals into the IoT device are:

**During manufacturing**  
If the security principals need to be injected during the manufacturing process, it is necessary to assess the security of the manufacturing supply chain. The objective is to determine the suitable stage in the manufacturing process where these principals can be generated or injected into the IoT device. It may be necessary to develop a factory utility tool to generate and inject the principals.

**During installation**  
If the security principals need to be injected during the installation and commissioning of IoT devices, it is crucial to develop an application, typically a mobile app, that includes features such as barcode scanning or serial number entry. When designing the workflow and app, it is important to evaluate the user persona involved, ensure usability, and consider the time required to complete all the necessary steps while maintaining the security of the entire process.

The principals generated and/or injected at any stage are not permanent; they require periodic renewal for security purposes. Therefore, the architecture must include audit and renewal mechanisms to ensure enduring security.

Both the AWS documentation and Azure documentation provide valuable information and guidelines on this topic. I have included links to the documentation in the references section below for further reading.

# Difference between Azure and AWS

**Azure** provides a managed service called **Azure Device Provisioning Service** (DPS), which extends Azure IoT Hub.

Azure DPS addresses multiple scenarios like

1. Zero-touch Provisioning (ZTP)
    
2. Load balancing
    
3. Multi-tenancy
    
4. Solution isolation
    
5. Geo-sharding
    
6. Ownership transfer
    
7. Re-provisioning.
    

Azure DPS is available at highly affordable pricing, for instance, in the east US2 region, it is $0.10 per thousand operations. This makes it an extremely cost-effective choice.

**AWS** offers IoT Core APIs and other necessary building blocks for constructing the required DPS service, along with vital documentation, whitepapers, and guidelines that include reference architectures for device provisioning setup. However, unlike Azure DPS, there is no consolidated managed service provided by AWS. It is the responsibility of the Architecture team to assemble and manage all the required building blocks. The cost of ownership for the device provisioning service may be slightly higher on AWS compared to Azure, although this may not be a significant factor.

In my opinion, Azure DPS is simpler to work with compared to AWS, where one has to put together multiple components.

Below are the references for further reading:

1. [AWS Single Device Provisioning](https://docs.aws.amazon.com/iot/latest/developerguide/single-thing-provisioning.html)
    
2. [Azure Single Device Registration](https://learn.microsoft.com/en-us/azure/iot-hub/quickstart-send-telemetry-cli#create-and-monitor-a-device)
    
3. [AWS Device Provisioning Options](https://docs.aws.amazon.com/iot/latest/developerguide/iot-provision.html)
    
4. [AWS Provisioning device identity in the manufacturing supply chain](https://docs.aws.amazon.com/whitepapers/latest/device-manufacturing-provisioning/provisioning-device-identity-in-the-manufacturing-supply-chain.html)
    
5. [Azure DPS Terminology](https://learn.microsoft.com/en-us/azure/iot-dps/concepts-service)
    
6. [AWS Zero Touch Provisioning and Device Lobby reference architectures](https://docs.aws.amazon.com/whitepapers/latest/device-manufacturing-provisioning/reference-architectures.html)
    
7. [AWS Global device provisioning](https://aws.amazon.com/blogs/iot/provision-devices-globally-with-aws-iot/)
    
8. [Azure IoT Hub Device Provisioning Service](https://learn.microsoft.com/en-us/azure/iot-dps/about-iot-dps)
    
9. [Azure TPM Quick start: Simulate TPM device registration](https://learn.microsoft.com/en-us/azure/iot-dps/quick-create-simulated-device-tpm?pivots=programming-language-ansi-c)
    
10. [Azure DPS TPM attestation](https://learn.microsoft.com/en-us/azure/iot-dps/concepts-tpm-attestation)
    
11. [AWS IoT Greengrass with TPM](https://aws.amazon.com/blogs/iot/using-a-trusted-platform-module-for-endpoint-device-security-in-aws-iot-greengrass/)
    
12. [Azure device authentication options](https://learn.microsoft.com/en-us/azure/iot-dps/concepts-device-oem-security-practices)
    
13. [AWS Device certification rotation](https://aws.amazon.com/blogs/iot/how-to-manage-iot-device-certificate-rotation-using-aws-iot/)
    
14. [Azure Device certificate rotation](https://learn.microsoft.com/en-us/azure/iot-dps/how-to-roll-certificates)
    
15. [LinkedIn article: AWS Mutual Authentication: How device trusts the Cloud endpoint?](https://www.linkedin.com/pulse/how-can-we-trust-aws-iot-core-lukasz-malinowski/?utm_source=share&utm_medium=member_android&utm_campaign=share_via)
