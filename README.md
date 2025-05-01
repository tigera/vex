# Tigera Vulnerability Exploitability Exchange (VEX)

This repository provides Vulnerability Exploitability eXchange ([VEX](https://www.cisa.gov/resources-tools/resources/when-issue-vex-information)) reports for Tigera's Calico, Calico Enterprise, and Calico Cloud product images. The VEX reports in this repository are intended to provide insights and vendor comments for [CVEs](https://www.cve.org/) that may appear in vulnerability scans of Tigera's product images. The VEX reports are **generated at the time of official release** for each product version, and are in [OpenVEX](https://github.com/openvex) format.

> **Note**: Reports include only official CVEs IDs and Github GHSA IDs, and do not include private source/third-party identifiers. 

> **Note**: This repository is not intended for CVE submissions. For CVEs inquires, please refer to [Tigera's Vulnerability Disclosure Policy](https://github.com/projectcalico/calico/security/policy).


# How to Use

Users can refer to these VEX reports to understand the analysis and mitigations applied to CVEs identified in Tigera products. The reports provides exploitability status and impact statement for known CVEs. Users can import the reports to provide additional context or filter the CVEs that do not affect Tigera products.

## Importing the VEX Document into Scanners

While scanner behavior may vary over time, VEX is currently supported by scanners such as [**Trivy**](https://github.com/aquasecurity/trivy) and [**Grype**](https://github.com/anchore/grype) as shown below. For the most up-to-date instructions or compatibility with other scanners, please refer to the official documentation of each tool.

> **Note**: VEX is a new feature and scanners may change their behavior in the future. As part of generating each VEX report, each report is verified by the latest version of Trivy and Grype to make sure it is compatible with the scanners at the time of release. 

### Using VEX with Trivy

`trivy image [your-image] --vex [path-to-VEX-document]` 

### Using VEX with Grype

`grype image [your-image] --vex [path-to-VEX-document]` 

> **Note:** Grype may require additional configuration to suppress the display of vulnerabilities that are marked as "not affected" in the VEX document. Make sure your `grype.yaml` configuration file is updated accordingly.


# Signature Verification

Each report includes a signature for the VEX document, which is digitally signed using [cosign](https://github.com/sigstore/cosign). As an optional security measure, you can verify the authenticity of each report before importing it into your scanner.

## Signature Verification Steps

1.  **Install cosign**  
    Follow the instructions in the [cosign GitHub repository](https://github.com/sigstore/cosign).
    
2.  **Run the verification command**  
    Use the following command to verify a signed VEX document:
    
    
    ```bash
    cosign verify-blob --key [path-to-Tigera-VEX-public-key] --signature [path-to-signature] [path-to-VEX-document] 
    ```

> Note: You can find the Tigera public key, VEX documents, and their corresponding signatures in this repository.