---
title: IEAK 11 and security
description: IEAK 11 and security
ms.assetid: 5b64c9cb-f8da-411a-88e4-fa69dea473e2
ms.prod: IE11
ms.mktglfcycl: plan
ms.sitesec: library
---

# IEAK 11 and security


Use Internet Explorer in conjunction with your new and existing security measures, to make sure the computers in your company aren’t compromised while on the Internet.

## <span id="Enhanced_Protection_Mode"></span><span id="enhanced_protection_mode"></span><span id="ENHANCED_PROTECTION_MODE"></span>Enhanced Protection Mode


Introduced in Internet Explorer 10, Enhanced Protected Mode applies new functionality to the existing Protected Mode processes. Including:

-   Restricting access to higher-level processes in the AppContainer. This is turned on by default for both IE and Internet Explorer for the desktop

-   Improving security against memory safety exploits in 64-bit tab processes. This is turned on by default for IE, but needs to be turned on for Internet Explorer for the desktop

## <span id="Certificates_and_Digital_Signatures"></span><span id="certificates_and_digital_signatures"></span><span id="CERTIFICATES_AND_DIGITAL_SIGNATURES"></span>Certificates and Digital Signatures


Web browsers have security features that help protect users from downloading harmful programs. Depending on the security level and the platform that you are using, the user may be prevented from, or warned against, downloading programs that are not digitally signed. Digital signatures show users where programs come from, verify that the programs have not been altered, and ensure that users do not receive unnecessary warnings when installing the custom browser.

Because of this, the custom .cab files created by the IE Customization Wizard 10 should be signed, unless you pre-configure the Local intranet zone with a Low security setting. Any custom components you distribute with your browser package for these platforms should also be signed.

### <span id="Understanding_certificates"></span><span id="understanding_certificates"></span><span id="UNDERSTANDING_CERTIFICATES"></span>Understanding certificates

To sign your package and custom programs digitally, you must first obtain a digital certificate. You can obtain a certificate from a certification authority or a privately-controlled certificate server. For more information about obtaining certificates or setting up a certificate server, see the following:

-   Microsoft-trusted certification authorities ([Windows root certificate program members](http://go.microsoft.com/fwlink/?linkid=59547)).

-   Certificates overview documentation ([Certificates](http://go.microsoft.com/fwlink/?linkid=68942)).

-   Microsoft Active Directory Certificate Services ( [Active Directory Certificate Services](http://go.microsoft.com/fwlink/?LinkId=259521)).

-   Enterprise public key infrastructure (PKI) snap-in documentation ([Enterprise PKI](http://go.microsoft.com/fwlink/?LinkId=259526)).

When you get a certificate, you should note the public and private keys, which are a matched set of keys that are created by the software publisher for encryption and decryption. They are generated on your computer at the time the certificate is requested, and your private key is never sent to the certification authority or any other party.

### <span id="Understanding_code_signing"></span><span id="understanding_code_signing"></span><span id="UNDERSTANDING_CODE_SIGNING"></span>Understanding code signing

-   **If you plan to distribute custom packages over the Internet**, you must sign all custom components and the CMAK profile package (if used). Before you start the IE Customization Wizard 11, make sure that both are signed. Typically, their respective manufacturers will have signed them. Otherwise, you can sign these using the Sign Tool (SignTool.exe) ( [SignTool.exe (Sign Tool)](http://go.microsoft.com/fwlink/?LinkId=71298)) or use the File Signing Tool (Signcode.exe) ([Signcode.exe (File Signing Tool)](http://go.microsoft.com/fwlink/?LinkId=71299)). You should read the documentation included with these tools for more information about all of the signing options.

    In addition, after you run the Internet Explorer 10 Customization Wizard, we highly recommend that you sign the IEAK package and the Branding.cab file (if you are using it separately from the package). You can do this also using the tools mentioned above.

    For more information, download Code-Signing Best Practices ([Code-Signing Best Practices](http://go.microsoft.com/fwlink/?LinkId=71300)).

-   **If you plan to distribute your custom packages over an intranet**, sign the custom files or preconfigure the Local intranet zone with a Low security setting, because the default security setting does not allow users to download unsigned programs or code.

### <span id="Understanding_your_private_key"></span><span id="understanding_your_private_key"></span><span id="UNDERSTANDING_YOUR_PRIVATE_KEY"></span>Understanding your private key

Your computer creates two keys during the enrollment process of your digital certificate. One is a public key, which is sent to anyone you want to communicate with, and one is a private key, which is stored on your local computer and must be kept secret. You use the private key to encrypt your data and the corresponding public key to decrypt it.

You must keep your private key, private. To do this, we recommend:

-   **Separate test and release signing.** Set up a parallel code signing infrastructure, using test certificates created by an internal test root certificate authority. This helps to ensure that your certificates aren’t stored on an insecure build system, reducing the likelihood that they will be compromised.

-   **Tamperproof storage.** Save your private keys on secure, tamper-proof hardware devices.

-   **Security.** Protect your private keys using physical security measures, such as cameras and card readers.

 

 




