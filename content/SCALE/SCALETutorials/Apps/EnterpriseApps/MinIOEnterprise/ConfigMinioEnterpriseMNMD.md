---
title: "Installing MinIO Enterprise MNMD"
description: "Provides instructions on installing and configuring MinIO Enterprise in a Multi-Node Multi-Disk (MNMD) configuration."
weight: 20 
aliases: 
tags:
- scaleminio
- scaleenterprise
---


{{< toc >}}

{{< enterprise >}}
The instructions in this article apply to the TrueNAS MinIO Enterprise application installed in a Multi-Node Multi-Disk (MNMD) multi mode configuration. 

SCALE Enterprise single controller systems with the applications and virtual machines license have access to the **MinIO Official Enterprise** widget. 
{{< /enterprise >}}

For more information on MinIO multi mode configurations see [MinIO Single-Node Multi-Drive (SNMD)](https://min.io/docs/minio/linux/operations/install-deploy-manage/deploy-minio-single-node-multi-drive.html) or [Multi-Node Multi-Drive (MNMD)](https://min.io/docs/minio/linux/operations/install-deploy-manage/deploy-minio-multi-node-multi-drive.html#minio-mnmd). MinIO recommends using MNMD (distributed) for enterprise-grade performance and scalability.

## Adding MinIO Enterprise App
Community members can add and use the MinIO Enterprise app or the default community version.

{{< include file="/_includes/AddMinioEnterpriseTrain.md" type="page" >}}

## First Steps
Complete these steps for every system (node) in the cluster. 
When creating the certificate, enter the system IP addresses for each system in **Subject Alternate Names**.

{{< include file="/_includes/MinIoEnterpriseFirstSteps.md" type="page" >}}

## Installing MinIO Enterprise
{{< hint info >}}
This procedure covers the required Enterprise MinIO App settings.
{{< /hint >}}

Repeat this procedure for every system (node) in the MNND cluster. 

{{< include file="/_includes/MinIoEnterpriseConfig1.md" type="page" >}}

Select the new **Certificates** created for MinIO from the dropdown list.

Enter the TrueNAS server IP address and the API port number 30000 as a URL in **MinIO Server URL (API**). For example, http://*ipaddress*:30000.
Enter the TrueNAS server IP address and the web UI browser redirect port number 30001 as a URL in **MinIO Browser Redirect URL**. For example, http://*ipaddres*:30001.

Scroll down to or click on **Storage Configuration** on the list of section at the right of the screen. 
Click **Add** three times in the **Storage Configuration** section to add three more sets of storage volume settings. 
In the first set of storage volume settings, select **Host Path (Path that already exists on the system)** and accept the default /data1 in **Mount Path**. 
Enter or browse to the data1 dataset to populate **Host Path** with the mount path. For example, */mnt/tank/apps/data1*.

{{< trueimage src="/images/SCALE/23.10/InstallMinIOSNMDStorageConfigData1andData2.png" alt="Add Storage Volumes /data1 And /data2" id="6: Add Storage Volumes /data1 And /data2" >}}

Scroll down to the next set of storage volume settings and select **Host Path (Path that already exists on the system)**. 
Change the **Mount Path** to /data2, and enter or browse to the location of the data2 dataset to populate the **Host Path**.

Scroll down to the next set of storage volume settings and select **Host Path (Path that already exists on the system)**. 
Change the **Mount Path** to /data3, and enter or browse to the location of the data3 dataset to populate the **Host Path**.

{{< trueimage src="/images/SCALE/23.10/InstallMinIOSNMDStorageConfigData3andData4.png" alt="Add Storage Volumes /data3 And /data4" id="7: Add Storage Volumes /data3 And /data4" >}}

Scroll down to the last set of storage volume settings and select **Host Path (Path that already exists on the system)**. 
Change the **Mount Path** to /data4, and enter or browse to the location of the data4 dataset to populate the **Host Path**.

Select **Enable Multi Mode (SNMD or MNMD)**, then click **Add**. 
Enter **https://*ipaddress*{1...4}:30000/data{1...4}** in the **Multi Mode (SNMD or MNMD)** field, and where ***ipaddress* is the IP Address for the system you are configuring. Separate the numbers in the curly brackets with three dots. 

{{< trueimage src="/images/SCALE/23.10/InstallMinIOAddMultiModeSNMD.png" alt="Multi Mode SNDN Command" id="8: Multi Mode SNDN Command" >}} replace image

{{< include file="/_includes/MinIoEnterpriseConfig2.md" type="page" >}}

{{< taglist tag="scaleminio" limit="10" title="Related MinIO Articles" >}}
{{< taglist tag="scaleenterprise" limit="10" title="Related Enterprise Articles" >}}