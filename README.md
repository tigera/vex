
  

# VEX Report for Tigera Products

  

This repository provides Vulnerability Exploitability eXchange ([VEX](https://www.cisa.gov/resources-tools/resources/when-issue-vex-information)) reports for Calico, Calico Enterprise, and Calico Cloud. Each report includes an analysis of vulnerabilities (CVEs) associated with these products (only high and critical vulnerabilities) that users may encounter when performing security scans. The VEX report is only generated at the time of official release for each version.

  

## Purpose

  

The VEX reports in this repository are intended to provide insights and detailed analysis for some public CVEs that may appear when users scan Tigera products. Reports are for high and critical CVES only. **Note**: These reports include only official CVEs (starting with "CVE-ID") and do not cover third-party identifiers such as PRISMA or GitHub IDs. We also expect all the users to use the latest patch version of a [supported version](https://github.com/projectcalico/calico/security/policy) in order to recieve all the security updates.

  

## How to Use

  

Users can refer to these VEX reports to understand the analysis and mitigations applied to CVEs identified in Tigera products. Each report provides an exploitability status and analysis for each CVE. Users can import reports (to their scanners) to automatically filter the CVEs that do not affect Tigera products.



### Importing the VEX Document into Scanners

While scanner behavior may vary over time, you can currently use VEX documents with tools like **Trivy** and **Grype** as shown below. For the most up-to-date instructions or compatibility with other scanners, refer to the official documentation of each tool.

#### Using VEX with Trivy

`trivy image [your-image] --vex [path-to-VEX-document]` 

#### Using VEX with Grype

`grype image [your-image] --vex [path-to-VEX-document]` 

> **Note:** Grype may require additional configuration to suppress the display of vulnerabilities that are marked as "not affected" in the VEX document. Make sure your `grype.yaml` configuration file is updated accordingly.

### Note

  

VEX is a new feature and scanners may change their behavior in the future. As part of generating each report, we check the report against the latest version of Trivy and Grype to make sure it is compatible with the scanners at the time of release. 


  

## Signature Verification


Each report includes a signature for the VEX document, which is digitally signed using [cosign](https://github.com/sigstore/cosign). As an optional security measure, you can verify the authenticity of each report before importing it into your scanner.

#### Signature Verification Steps

1.  **Install cosign**  
    Follow the instructions in the [cosign GitHub repository](https://github.com/sigstore/cosign).
    
2.  **Run the verification command**  
    Use the following command to verify a signed VEX document:
    
    
    ```bash
    cosign verify-blob --key [path-to-Tigera-VEX-public-key] --signature [path-to-signature] [path-to-VEX-document] 
    ```

> Note: You can find the Tigera public key, VEX documents, and their corresponding signatures in this repository.

