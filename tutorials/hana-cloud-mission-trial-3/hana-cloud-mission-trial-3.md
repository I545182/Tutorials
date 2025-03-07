---
parser: v2
author_name: Dan van Leeuwen
author_profile: https://github.com/danielva
auto_validation: true
time: 10
tags: [ tutorial>beginner, software-product>sap-hana-cloud, software-product-function>sap-hana-cloud\,-sap-hana-database]
primary_tag: software-product>sap-hana-cloud
---

# Provision an Instance of SAP HANA Cloud, SAP HANA Database
<!-- description --> Learn how to provision an instance of SAP HANA Cloud, SAP HANA database.

## Prerequisites
- You have access to [SAP HANA Cloud trial](hana-cloud-mission-trial-2), [SAP HANA Cloud free tier](hana-cloud-mission-trial-2-ft), or a production environment of SAP HANA Cloud, SAP HANA database


## You will learn
- How to provision an instance of SAP HANA Cloud, SAP HANA database

## Intro
A few notes to remember about free tier model and trial accounts:

-	If you are using a free tier model or trial account, you will only be able to create one instance with a predefined size (32 GB of memory, 2 vCPUs, and 120 GB of storage for free tier and 16 GB of memory, 1 vCPU, and 80 GB of storage for trial). However, the process to create the instance is very similar to production environments, the difference being that in a production environment you have the ability to further customize your instance. For example, you are able to change advanced settings for your SAP HANA Cloud instance.  

-	Free tier model and trial instances will be **stopped on a nightly basis**. Each time you start working with your free tier model or trial instance, you need to restart it.

-	If you do not restart your trial instance within **30 days**, it will be **deleted**. Your BTP account, however, will continue to exist and you can easily provision an instance again, if you wish to do so.

- The instance summary card: Trial (left) and free tier (middle) does not display a cost estimate. If you are using free tier, ensure you see the free tier indicator icon since paid tier (right) will show you a cost estimate meaning charges will be incurred if you create an instance.

    ![Summary Card Differences](estimate.png)

---

### Start the Provisioning Wizard

To create your first instance of SAP HANA Cloud, SAP HANA database, you need to follow these steps:

1. In SAP BTP cockpit, open SAP HANA Cloud Central by clicking on the subscription to SAP HANA Cloud in the **Subscriptions** tab. 

    ![HCC ME tooling](hcc-app.png)

2.	On the top-right corner of the screen, click on **Create Instance**.

    ![Create instance in SAP HANA Cloud Central](hcc-create-instance.png)

3.	Here you must choose the **Type** of instance to create.  Select **SAP HANA Cloud, SAP HANA Database**.

    > If you would like to learn more about **SAP HANA Cloud, Data Lake**, and [Get Started with a Standalone SAP HANA Cloud, Data Lake](mission.hana-cloud-data-lake-get-started), navigate to the linked mission for the basics.

    ![Provisioning Wizard](wizard-type.png)

    You may also choose the runtime environment.  Further details can be found at [What Runtime Environment is my SAP HANA Cloud Instance Using?](https://help.sap.com/docs/hana-cloud/sap-hana-cloud-administration-guide/runtime-environments-for-sap-hana-cloud). 

4.	Click on **Next Step** to continue.

### Choose your license, instance name, and password

1. If you have multiple types of service plans enabled in your SAP HANA Cloud entitlement, a **License** section will appear just before the Basics section. To use the free tier model, click on **Free Tier** so that it is highlighted as shown below. Note that if you have enabled only one type of service plan in your SAP HANA Cloud entitlement (e.g. free tier only), the License section does not appear and that service plan type will be used automatically.

    ![Free tier option](select-ft.png)

2.	In the **Basics** section, enter a name for your instance in the field **Instance Name**, such as `HC_HDB`.

    > This field does not allow any spaces in the name. Keep in mind that you will not be able to change the name after the instance has been created.

3.	Insert a password in the **Administrator Password** field.

4.	Confirm it by typing it again in the **Confirm Administrator Password** field.

    ![HANA step 1](hdb-instance-name.png)

    > This password is the admin password for this instance, so make sure to use a strong password.  If needed, the password can be reset via the actions menu [Reset DBADMIN Password](https://help.sap.com/docs/HANA_CLOUD/9ae9104a46f74a6583ce5182e7fb20cb/649092e9d9be41c59930179ce4f3d59e.html?locale=en-US) in SAP HANA Cloud Central if your user has the role SAP HANA Cloud Security Administrator.

5.	Now click on **Next Step** to continue.  


### Set up the size of your database

> There are different instructions available to you depending on whether you are using a free tier model or trial account versus a production environment. Please make sure to select the one that applies to your situation to get the most out of this tutorial.

In this step of the provisioning wizard, you can set up the size of your SAP HANA database in SAP HANA Cloud.

[OPTION BEGIN [Production]]

In a production environment, you are able to select a performance class and choose the initial size of your instance.

1.	Here, you can select how much **Memory** you wish to allocate to this instance.

    ![HDB Memory](2-ss-04-HDB-Memory.png)

    As you increase your memory requirements, the **Compute** and **Storage** values will be automatically adjusted as well.

    Follow this [link](https://help.sap.com/docs/hana-cloud/sap-hana-cloud-administration-guide/sap-hana-database-size) to learn more about the memory allocation.

2.	Click on **Next Step** to continue.

[OPTION END]

[OPTION BEGIN [Free Tier/Trial]]

For a free tier instance, the size allocation is predefined to 32 GB for memory, 120 GB for storage and 2 vCPUs for computation.

For a trial instance, the size allocation is predefined to 16 GB for memory, 80 GB for storage and 1 vCPU for computation.

![SAP HANA Database Memory Allocation](hdb-memory2.png)

Click on **Next Step** to continue.

[OPTION END]


### Specify database availability zone and replicas

> There are different instructions available to you depending on whether you are using a free tier model or trial account versus a production environment. Please make sure to select the one that applies to your situation to get the most of this tutorial.

Here, you can select in this step if you want to create **replicas** of your instance to increase your system availability. These replicas are exact duplicates of your instance that will be managed in the background and automatically synchronized. In case of issues, you can take over a replica of your instance to ensure minimal interruption.

[OPTION BEGIN [Production]]

1.	Select the availability zone for your instance and optionally, include a replica.

    ![Availability Zone](avail-zone2.png)

    To read more about increasing system availability, you can check this [technical documentation](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-administration-guide/increasing-system-availability).

2.	Click on **Next Step** to continue.

    > Keep in mind that you cannot change the **availability zone of the instance** after it has been created. To update replicas, you need to delete and re-create the instance.

[OPTION END]
[OPTION BEGIN [Free Tier/Trial]]

In a free tier model or trial environment, availability zone and replicas are not supported.

![HANA database replicas](hdb-replicas2.png)

To read more about increasing system availability, you can check this [technical documentation](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-administration-guide/increasing-system-availability).

Click on **Next Step** to continue.

> Keep in mind that you cannot change the availability zone of the instance after it has been created. To update replicas, you need to delete and re-create them.

[OPTION END]



### Check the advanced settings

> There are different instructions are available to you depending on whether you are using a free tier model or trial account versus a production environment. Please make sure to select the one that applies to your situation to get the most of this tutorial.

[OPTION BEGIN [Production]]

1.	Under **Advanced Settings**, you can choose to enable the **Script Server**, **Document Store**, and **Data Provisioning Server**. If your database does not have the required `vCPUs` for either of the first two options, you can click on the link on the error message, which will change your original setup and add more `vCPUs` automatically.

    ![Advanced Settings](prod-advanced-settings2.png)

2.	You can now manage the allowed connections for your SAP HANA database instance, i.e., you can choose to allow access to your SAP HANA database instance from outside of the SAP Business Technology Platform. You can either limit it to SAP Business Technology Platform by denying all IP addresses, or allow specific applications to access it by inserting one or more specific IP addresses. Finally, you can also allow all connections from all IP addresses.

3.	Next, you can also choose to enable the **SAP Cloud Connector**, which makes it easier to connect this SAP HANA database instance to an SAP HANA on-premise database.

    > To get familiar with the **Cloud Connector**, you can check the [technical documentation](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector).
    >
    >Select whether you want your SAP HANA database to connect to your on-premises remote sources through the cloud connector. For details, see the [SAP HANA Database Connectivity Documentation](https://help.sap.com/docs/hana-cloud-database/sap-hana-cloud-sap-hana-database-data-access-guide/data-access-in-sap-hana-cloud-sap-hana-database?locale=en-US).
    >
    > Keep in mind that you can still change your configurations here at a later point, if you decide to do so.  

4.	Click on **Next Step** in the bottom left corner to continue.

[OPTION END]
[OPTION BEGIN [Free Tier/Trial]]

Now you can configure the **Advanced Settings**.

1. The Predictive Analysis Library (PAL) is not required for this tutorial mission.  Further details can be found at [Hands-on Tutorial: Machine Learning with SAP HANA Cloud](https://community.sap.com/t5/artificial-intelligence-and-machine-learning-blogs/hands-on-tutorial-machine-learning-with-sap-hana-cloud/ba-p/13683430).

2. The Data Provisioning Server is not required in this tutorial mission.

3.	You may manage the allowed connections for your SAP HANA database instance, i.e. allowing access to your SAP HANA database instance from outside of the SAP Business Technology Platform (SAP BTP). Selecting Allow only BTP IP addresses denies all IP addresses outside SAP BTP. You may choose to allow access to specific applications by inserting one or more specific IP addresses or you can allow connections from all IP addresses.

4.	Next, you can also choose to enable the SAP Cloud Connector, which makes it easier to connect this SAP HANA database instance to an SAP HANA on-premises database. You can also set the connection preferences for your cloud connector under **Allowed connections**.

    > Keep in mind that you can still change your configurations here at a later point, if you decide to do so.  

    ![HDB advanced settings](hdb-advanced-settings2.png)

5. We will be using the instance mapping feature later in this tutorial mission.  Instance mapping enables an instance provisioned into the SAP BTP subaccount to be mapped into a runtime environment such as Cloud Foundry.

6.	Click on **Next Step** in the bottom left corner to continue.

[OPTION END]


### Enable the SAP HANA Cloud, data lake (optional)

In the last step of the provisioning wizard, you have the option of also provisioning a managed data lake. If you enable the data lake in this step, this data lake will have maximum compatibility with SAP HANA and a remote connection between your SAP HANA database and the data lake will be created automatically during provisioning.

> If you do not wish to enable a data lake, you can skip this step by clicking on **Review and Create** in the bottom-right corner.

[OPTION BEGIN [Production]]
1.	If you click on **Create data lake**, a managed SAP HANA Cloud, data lake will be provisioned alongside your SAP HANA database in SAP HANA Cloud and will include a data lake Files instance.

    ![Data Lake Enabled](hdl-prod-create2.png)

2.	Next, give your data lake instance a name under **Instance Name**.

    ![Data lake name](hdl-prod-name2.png)

    > When you add a managed data lake, the HDLADMIN user is automatically created and is given the same password as DBADMIN, which you set in the first step. If later you decide to change the password of one user, the password of the other user will **not** be automatically changed.   

3.	Click on **Next Step** to continue.

4.	This is where you can adjust how many **coordinators** and **workers** you want for your data lake, as well the amount of **storage** you wish to allocate to this instance.

    ![Data Lake IQ](hdl-prod-dlre2.png)

    > The coordinator and worker size, as well as the number of workers will affect instance pricing. For details, see SAP HANA Cloud Capacity Unit Estimator.

5.	Click on **Next Step** to continue.

6.	Now you can set up the **Advanced Settings** for the data lake. Here you can manage the allowed connections and choose - just like you did for your SAP HANA database in SAP HANA Cloud - if you want to allow only BTP IP addresses, all IP addresses or, specific IP addresses. The last option also gives you the option to **Copy IP addresses from the SAP HANA database** choosing again, who can have access to your data lake instance.

    ![HDL Connections](hdl-prod-review2.png)

7.	Lastly, click on **Review and Create** to finish the provisioning process.

[OPTION END]
[OPTION BEGIN [Free Tier/Trial]]

1.  Once you select **Create Data Lake** option, two more menu options will appear in the wizard with additional steps.  Note that a data lake Files instance is not included in free tier or trial.

    ![Create Data Lake](hdl-create2.png)

2. Next, give your data lake instance a name under **Instance Name**.

    >When you add a managed data lake, the HDLADMIN user is automatically created and is given the same password as DBADMIN, which you set in the first step. If later you decide to change the password of one user, the password of the other user will **not** be automatically changed.   

    ![Name Data Lake](hdl-name2.png)

3.	In production environment this is where you can adjust how many **coordinators** and **workers** you want for your data lake, as well the amount of **storage** you wish to allocate to this instance. But in a free tier model or trial account, you can't change these as they are predefined settings.

    > Please remember that you can enable or disable the data lake later as well if you prefer.
    >
    > The coordinator and worker size, as well as the number of workers will affect instance pricing. For details, see [SAP HANA Cloud Capacity Unit Estimator](https://hcsizingestimator.cfapps.eu10.hana.ondemand.com/).

    ![Data lake size](hdl-size2.png)

4.	Click on **Next Step** to continue.

5.	Now you can set up the **Advanced Settings** for the data lake instance. Here you can manage the allowed connections and chose - just like for your SAP HANA database in SAP HANA Cloud - if you want to allow only BTP IP addresses, all IP addresses or specific IP addresses.

    Note that backups are not available for instances under free tier or trial accounts.

    ![Data lake advanced](hdl-advanced2.png)

6.	Lastly, click on **Review and Create** to finish the provisioning process and **Create Instance**.

    ![Data Lake Create Instances](hdl-create-instance2.png)

[OPTION END]


You are done! Your first SAP HANA Cloud, SAP HANA database and data lake instances will be created, and you can monitor their status to see when they will be ready to be used. This process usually takes a few minutes.


### Start and stop your instance

The final step is learning how to stop and start your instance.

> In a free tier or trial account, your instance will be automatically stopped on a nightly basis, according to the server region time zone. That means you need to restart your instance before you start working with your free tier model or trial every day.

1.	To stop an instance, just click on **Stop** in the three dots menu next to the SAP HANA Cloud instance line in SAP HANA Cloud Central. Once your instance is stopped, the menu item will be updated to **Start**.

    ![Three Dots](three-dots2.png)

2.	To restart the instance, simply click on the **Start** menu item. Once it's ready to be used, it will show a green **Created** status on SAP BTP Cockpit, and a **Running** status on the SAP HANA Cloud Central.

>Note that all these processes take a few minutes to be completed and to show an updated status. You can use the auto-refresh button to select how often you would like your instances list to periodically refresh.

>   ![Refresh Instances](time-refresh2.png)
>

### Upgrade to Paid Tier (Free Tier Only)

When you are ready to upgrade your free tier instance to Paid Tier, you can also choose the three dots menu (under Actions) next to the SAP HANA Cloud instance line in SAP HANA Cloud Central.  From here, click on **Upgrade to Paid Tier**.  Note that paid tier plans must be enabled in your SAP HANA Cloud entitlement in order for the **Upgrade to Paid Tier** menu item to appear.

![upgrade to paid tier](upgrade-paid-tier-2.png)

A dialog box will appear indicating that there will be costs associated with the Paid Tier instance – an estimate is also included.  Click on **Upgrade to Paid Tier** to complete the process.

![upgrade to paid tier](upgrade-paid-tier-confirm.png)

Now you know how to provision an instance of SAP HANA Cloud using SAP BTP Cockpit and SAP HANA Cloud Central. In the next tutorial, learn about the tools that help to manage and access your database instance.


### Knowledge Check





---
