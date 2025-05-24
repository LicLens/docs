---
description: >-
  If you do not use Extension Attributes in Active directory to store custom
  user attributes, you can map such attributes to the reports by uploading a
  mapping file.
---

# Upload Custom Attributes

{% hint style="info" %}
If you use Extention Attributes in Active Directory, we recommend you use '[Update Custom Attribute](update-custom-attributes.md)' feature. This article is for users who do not use Extension Attributes in AD.
{% endhint %}

In environments where custom user attributes are not stored in **Active Directory's Extension Attributes**, organizations can still incorporate these attributes into their reporting workflows. This can be achieved by using attribute mapping files.

## Why Use a Mapping File?

Custom attributes such as department codes, cost centers, or project IDs are often managed outside of AD. Incorporating these attributes into reports is critical for IT administrators, finance teams, and decision-makers to achieve:

* **Enhanced Cost Allocation**: Map users to their respective cost centers.
* **Streamlined Department Analysis**: Segment data by team or department for better insights.
* **Customized Reporting**: Include organization-specific attributes that are not natively available in AD.

## How to prepare the Mapping file?

The mapping file is a CSV file containing the unique user identifier (such as `UserPrincipalName` or `EmployeeID`) and the corresponding custom attributes. For example:

`UserPrincipalName,Cost Center,Department Code`\
`john.doe@company.com,CC101,ABC123`\
`jane.smith@company.com,CC102,XYZ987`

[Download a Sample CSV File](https://365TUNE.com/downloads/samples/attributes_mapping.csv)

## How to upload the Mapping file?

Go to the **Mapping File Upload** section and select your prepared CSV file. The app automatically validates the file to ensure the data is formatted correctly and matches the user identifiers in account.

## **How to add Custom Attributes in Reports?**

* Select the desired report (e.g., All Users Report).
* on the top right section, locate and click on the **Columns** button.
* From the drop down, Check the box for the custom attributes you wish to include in the report.

<figure><img src="../../.gitbook/assets/image (4).png" alt="" width="563"><figcaption></figcaption></figure>

By utilizing the custom attributes feature, 365TUNE empowers organizations to gain deeper insights into their license usage and optimize financial and operational reporting processes. For further assistance, **Contact Support**.
