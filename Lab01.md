# Exercise 1 - Create a storage account using Azure portal
Use the Azure portal to create a storage account

- **Login** to [Azure portal](https://portal.azure.com) using the credentials provided in the environment details page. You will be having access to one resource group.</br>
- On the Azure portal menu or from the **Home** page, select **Create a resource**.
- Select **Storage** under **Azure Marketplace** and click select **Storage account**.<br/>
 
  <img src="images/str1.jpg"/><br/>
 
 **Under PROJECT DETAILS:**
- In the Subscription field, select the **subscription** in which to create the storage account
- Select the existing Resource Group **odl-demo-xxxx** from the drop-down list.
Under **INSTANCE DETAILS:**
- Enter a **Storage account name**. The name will be used to generate the public URL used to access the data in the account. The name must be unique across all existing storage account names in Azure. Names must be 3 to 24 characters long and can contain only lowercase letters and numbers.

- Select a **Location** same as **Resource Group** Location.

- Select Standard for the **Performance** option. This decides the type of disk storage used to hold the data in the Storage account.

- Select StorageV2 (general purpose v2) for the **Account kind**. This provides access to the latest features and pricing. In particular, Blob storage accounts have more options available with this account type. You need a mix of blobs and a queue, so the Blob storage option will not work. For this application, there would be no benefit to choosing a Storage (general purpose v1) account, since that would limit the features you could access and would be unlikely to reduce the cost of your expected workload.

- Select Locally-redundant storage (LRS) for the **Replication** option. Data in Azure storage accounts are always replicated to ensure high availability - this option lets you choose how far away the replication occurs to match your durability requirements.

- Set the **Access tier** to Hot. This setting is only used for Blob storage. The **Hot Access Tier** is ideal for frequently accessed data, and the **Cool Access Tier** is better for infrequently accessed data.

The following screenshot shows the completed settings for the **Basics** tab. Note that the resource group, subscription, and name will have different values.

<img src="images/str2.jpg"/><br/>
      
# Configure the networking options

1. Click the **Next: Networking >** button to move to the **Networking** tab, or select the **Networking** tab at the top of the screen.
2. Set the **Connectivity** method option to Public endpoint (all networks). This option allows you to isolate the storage account on an Azure virtual network. We want to use public Internet access. Our content is public facing and you need to allow access from public clients.

<img src="images/str3.jpg"/><br/>

# Configure the advanced options 
1. Click the **Next: Advanced >** button to move to the **Advanced** tab, or select the **Advanced** tab at the top of the screen.

2. Set **Secure transfer required** to Enabled. The **Secure transfer required** setting controls whether **HTTP** can be used for the REST APIs used to access data in the Storage account. Setting this option to Enabled will force all clients to use SSL **(HTTPS)**. Most of the time you'll want to set this to Enabled as using HTTPS over the network is considered a best practice.

3. **Leave the Large** file shares option set to Disabled. Large file shares provides support up to a 100TiB, however this type of storage account can't convert to a Geo-redundant storage offering and upgrades are permanent.

4. Leave the **Blob Soft delete** option set to Disabled. Soft delete lets you recover your blob data in many cases where blobs or blob snapshots are deleted accidentally or overwritten.

5. Leave the **Data Lake Storage Gen2** option as Disabled. This is for big-data applications that aren't relevant to this module.

The following screenshot shows the completed settings for the **Advanced** tab.

<img src="images/str4.jpg"/><br/>

### Create

1. Click **Review + create** to review the settings. This will do a quick validation of your options to make sure all the required fields are selected. If there are issues, they'll be reported here. Once you've reviewed the settings, click **Create** to provision the storage account.

It will take a few minutes to deploy the account. While Azure is working on that, let's explore the APIs we'll use with this account.

### Verify

1. Select the **Storage accounts** link in the left sidebar.
2. Locate the new storage account in the list to verify that creation succeeded.
# Exercise 2 - Create a Container and Upload file using Azure portal

To create a container in the Azure portal, follow these steps:

1. Navigate to your new storage account in the Azure portal.
2. In the left menu for the storage account, scroll to the **Blob service** section, then select **Containers**.
3. Select the + **Container** button.
4. Type a name for your new container. The container name must be lowercase, must start with a letter or number, and can include only letters, numbers, and the dash (-) character. For more information about container and blob names, see Naming and referencing containers, blobs, and metadata.
5. Set the level of public access to the container. The default level is **Private (no anonymous access).**
6. Select **OK** to create the container.

<img src="images/str5.jpg"/><br/>

## Upload a block blob

Block blobs consist of blocks of data assembled to make a blob. Most scenarios using Blob storage deploy block blobs. Block blobs are ideal for storing text and binary data in the cloud, like files, images, and videos. This quickstart shows how to work with block blobs.

To upload a block blob to your new container in the Azure portal, follow these steps:

1. In the Azure portal, navigate to the container you created in the previous section.
2. Select the container to show a list of blobs it contains. Since this container is new, it won't yet contain any blobs.
3. Select the **Upload** button to open the upload blade.
4. Browse your local file system to find a file to upload as a block blob.

<img src="images/str7.jpg"/><br/>

5. Optionally, expand the advanced section to define other setting such as authentication type, access tier, or virtual folder path.
6. Select the **Upload** button to commit the upload.
7. Upload as many blobs as you like in this way. You'll see that the new blobs are now listed within the container.

## Download a block blob

You can download a block blob to display in the browser or save to your local file system. To download a block blob, follow these steps:

1. Navigate to the list of blobs that you uploaded in the previous section.
2. Right-click the blob you want to download, and select **Download.**

