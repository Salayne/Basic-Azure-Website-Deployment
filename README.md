# Basic-Azure-Website-Deployment
Deploy a static website using  Azure Storage.

## STEP 1: Prepare Your Website Files
First, make sure you have all the files for your static website ready. This typically includes an index.html file, along with any CSS, JavaScript, and image files. Organize these files into a single folder on your local machine.  

## STEP 2: Create an Azure Storage Account
You'll use Azure Storage to host your website's content.
Log in to the Azure Portal.
Search for and select "Storage accounts".
Click "Create".
Fill in the required details:
Subscription: Choose your Azure subscription.
Resource group: Create a new one or select an existing one. A resource group is a container that holds related Azure resources.
Storage account name: This must be globally unique. Choose a name like mywebsite123.
Region: Select a region close to your users.
Performance: Choose Standard.
Redundancy: Choose Locally-redundant storage (LRS) for a simple project.
Click "Review + create" and then "Create".

## STEP 3: Enable Static Website Hosting
Once the storage account is created, you need to enable the static website feature.
Navigate to your new storage account.
In the left-hand menu, under "Data management", select "Static website".
Click "Enabled".
Set the Index document name to index.html and the Error document path to 404.html (or a file of your choice).
Click "Save". Azure will now provide you with a primary endpoint URL for your website.

## STEP 4: Upload Your Website Files
Now, upload your website's content to the storage account.
In the left-hand menu of your storage account, under "Data storage", select "$web".
Click the "Upload" button.
Select all the files and folders from your local website directory and upload them.
After the upload is complete, you can visit the primary endpoint URL you received in the previous step to see your website live!

***TROUBLESHOOTING***
If you come across an error like this:

 <Error>
<Code>PublicAccessNotPermitted</Code>
<Message>Public access is not permitted on this storage account. RequestId:45a03fed-301e-0075-5e49-0eeeb0000000 Time:2025-08-16T01:03:00.0734121Z</Message>
</Error>

**This is not recommended for sensitive data.**
At the Storage Account Level: In the Azure portal, navigate to your storage account, go to Settings > Configuration, and set "Allow Blob anonymous access" to Enabled. Note that this setting overrides all individual container settings and allows anonymous access to any container configured for public access.
At the Container Level: Once public access is allowed at the storage account level, you can set the public access level for individual containers. In the Azure portal, navigate to the container and change its public access level to "Blob" (anonymous read access for blobs only) or "Container" (anonymous read access for the container and its blobs).
