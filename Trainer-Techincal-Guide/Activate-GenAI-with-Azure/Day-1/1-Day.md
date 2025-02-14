# Challenge 01: Deploy Azure OpenAI Service and LLM Models
### Estimated Time: 30 minutes
## Introduction

Welcome to the Deploy Azure OpenAI Service Challenge! This challenge is designed to test your skills in deploying the Azure OpenAI Service and its Large Language Models (LLM). The goal is to set up the OpenAI Service and deploy LLM models.

**Azure OpenAI Service** provides REST API access to OpenAI's powerful language models, including the GPT-4, GPT-4 Turbo with Vision, `gpt-35-turbo`, and Embeddings model series. In addition, the new `GPT-4` and `gpt-35-turbo` model series have now reached general availability.

A **Large Language Model (LLM)** is a deep learning algorithm that can perform a variety of natural language processing (NLP) tasks. Large language models use transformer models and are trained using massive datasets—hence, large. This enables them to recognize, translate, predict, or generate text or other content.

**Contoso Ltd.**, a leading technological firm, is seeking to enhance its product support operations. They receive a vast number of queries daily, which results in longer waiting times and decreased customer satisfaction. To address this, Contoso is planning to implement an AI-powered solution that can handle customer inquiries effectively and efficiently.

They have chosen to deploy Azure OpenAI Service along with its Large Language Models (LLM), like `gpt-35-turbo` and `text-embedding-ada-002`. These models are known for their capability of processing and generating human-like text, making them ideal for this application.

As a part of this challenge, your task is to create an Azure OpenAI service and deploy Large Language Models (LLM). The Large Language Models include **gpt-35-turbo** and **text-embedding-ada-002**.

## Description

Your task is to deploy the Azure OpenAI Service and deploy Large Language Models (LLM).

### Accessing the Azure portal

>**Important**: You can find the Username and Password within the environment by navigating to the **Environment** **(1)** tab in the left pane then copy the **Azure Username** **(2)** and **Azure Password** **(3)**, which will be required for signing into the Azure portal in later steps and you can record the **Deployment Id** **(4)**, which can be used to provide a unique name to the resources during deployment.

>**Note**: Numbers and ID's values may vary kindly ignore values in screenshots and copy values from **Environment** tab.

 ![](../media/Active-image19.png)
 ![](../media/Active-image(20).png)

1. To access the Azure portal, within labvm open **Microsoft Edge** and browser to the [Azure Portal](https://portal.azure.com/).

1. On the **Sign into Microsoft Azure tab**, you will see a login screen. Enter the following email/username, and then click on **Next**
   
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

     ![](../media/Active-image1.png)

1. Now enter the following password and click on **Sign in**.

   - **Password:** <inject key="AzureAdUserPassword"></inject>

      ![](../media/Active-image2.png)

1. When **Action Required** window pop up click on **Ask Later**.

    ![](../media/Active-image3.png)
   
1. If you see the pop-up **Stay Signed in?**, click **No**.

    ![](../media/Active-image4.png)

1. If a **Welcome to Microsoft Azure** pop-up window appears, click **Cancel** to skip the tour.

    ![](../media/Active-image5.png)

## Prerequisites

- [Azure Subscription](https://azure.microsoft.com/en-us/free/)
- [Azure OpenAI](https://aka.ms/oai/access) access is available with the following models:
  - gpt-35-turbo
  - text-embedding-ada-002

## Solution Guide

### Task 1: Deploy an Azure Open AI Service

In this task you'll learn the process of setting up and deploying the Azure OpenAI service within the Azure Portal.

1. On Azure Portal page, in Search resources, services and docs (G+/) box at the top of the portal, enter **Azure OpenAI (1)**, and then select **Azure OpenAI (2)** under services.

    ![](../media/solt1s1.png)

1. On **Azure AI Services | Azure OpenAI (1)** blade, click on **+ Create (2)**.

   ![](../media/solt1s2.png)

1. Specify the following details to deploy the Azure Open AI service and click **Next** thrice.

   | **Option**         | **Value**                                              |
   | ------------------ | -----------------------------------------------------  |
   | Subscription       | Leave default                                          |
   | Resource Group     | **ODL-GenAI-CL-XXXXXXX-01**                 |
   | Region             | Use the same location as the resource group            |
   | Name               | Use the format **OpenAI-xxxxxx** (replace **xxxxxx** with the **Deployment ID**) |
   | Pricing tier       | **Standard S0**                                        | 

   >**Note**: Here, xxxxxx refers to the **deployment ID** which you recorded in last task.

    ![](../media/aigen1.png)

1. Once validation is successful on the **Review + submit** tab, click **Create** and wait for the deployment to complete.

     ![](../media/aigen2.png)

### Task 2: Deploy a model

Azure OpenAI provides a web-based portal named Azure OpenAI Studio, that you can use to deploy, manage, and explore models. You'll start your exploration of Azure OpenAI by using Azure OpenAI Studio to deploy a model.

1. On Azure Portal page, in Search resources, services and docs (G+/) box at the top of the portal, enter **Azure OpenAI (1)**, and then select **Azure OpenAI (2)** under services.

   ![](../media/solt1s1.png)

1. On **Azure AI Services | Azure OpenAI (1)** blade, select **OpenAI-<inject key="Deployment-id" enableCopy="false"></inject> (2)**.

    ![](../media/solt2s2.png)

1. In the Azure OpenAI resource pane, select **Overview** from the left-hand menu, then click on **Go to Azure AI Foundry Portal**. This will navigate you to Azure AI Studio.

   ![](../media/a19.png)

   >**Note :** If the pop-up Discover an even better Azure AI Studio experience appears, click Close to dismiss it.

1. Click on **Deployments (1)** under **Shared Resources**, then select **+ Deploy Model (2)**. Next, **choose Deploy Base Model (3)**.

    ![](../media/a20.png)

1. Search for **gpt-35-turbo** and click on **Confirm**.

    ![](../media/solimage2.png)

1. Within the Deploy model pop-up interface, click on **Customize** and enter the following details:
      - Deployment name: **text-turbo (1)**
      - Deployment type: **Standard (2)**
      - Model version: **0125(Default) (3)**
      - Tokens per Minute Rate Limit (thousands): **20K (4)**
      - Enable dynamic quota: **Enabled (5)**
      - Click on **Deploy (6)**.
        
        ![](../media/a24.png)

        >**Note:** If the **Customize** option doesn't appear, you can directly enter the model deployment details. 

1. Back on the **Deployments (1)** page again, then select **+ Deploy Model (2)**. Next, **choose Deploy Base Model (3)**.

     ![](../media/a20.png)

1. Search for **text-embedding-ada-002** and click on **Confirm**.

     ![](../media/solimage6.png)

1. Within the Deploy model pop-up interface, click on **Customize** and enter the following details:
      - Deployment name: **text-ada-002 (1)**
      - Deployment type: **Standard (2)**
      - Model version: Use the **default version (3)**
      - Tokens per Minute Rate Limit (thousands): **20K (4)**
      - Enable dynamic quota: **Enabled (5)**
      - Click on **Deploy (6)**
        
        ![](../media/solimage7.png)

        >**Note:** If the **Customize** option doesn't appear, you can directly enter the model deployment details. 

1. Back on the Deployments page, you should see the deployment models **text-turbo** and **text-ada-002** created.

## Success Criteria:

- Successful deployment of the Azure OpenAI Service.

- Deploying Large Language Models (LLM) with the OpenAI Service.


## Additional Resources:

- Refer to the [Azure OpenAI Service documentation](https://learn.microsoft.com/en-us/azure/ai-services/openai/) for guidance on deploying the service.

## Proceed with the next Challenge by clicking on **Next**>>...

# Challenge 02: Implement Document Search with Azure AI Search

### Estimated Time: 120 minutes

## Introduction:

All organizations rely on information to make decisions, answer questions, and function efficiently. The problem for most organizations is not a lack of information but the challenge of finding and  extracting the information from the massive set of documents, databases, and other sources in which the information is stored.

For example, suppose *Margie's Travel* is a travel agency that specializes in organizing trips to cities around the world. Over time, the company has amassed a huge amount of information in documents such as brochures as well as reviews of hotels submitted by customers. This data is a valuable source of insights for travel agents and customers as they plan trips, but the sheer volume of data can make it difficult to find relevant information to answer a specific customer question.

To address this challenge, Margie's Travel can use Azure AI Search to implement a solution in which the documents are indexed and enriched by using AI skills to make them easier to search.

## Solution Guide

### Task 1: Clone the repository for this course

If you have not already cloned the **mslearn-knowledge-mining** code repository to the environment where you're working on this lab, follow these steps to do so. Otherwise, open the cloned folder in Visual Studio Code.

1. Open **Visual Studio Code** from the Lab VM desktop by double-clicking on it.

1. In **Visual Studio Code**, from the top left menu, select the **(...) (1)** ellipses > **Terminal (2)**, then choose **New Terminal (3)**.

   ![](../media/Active-image42.png)

1. Execute the following command in the terminal to clone the repository to a local folder: (it doesn't matter which folder).

   ```
   git clone https://github.com/CloudLabsAI-Azure/mslearn-knowledge-mining.git
   ```
    ![](../media/ai-14.png)

1. When the repository has been cloned, open the folder in Visual Studio Code by following these steps:

    - From the top left corncer menu select **File (1)** > **Open Folder (2)**.

       ![](../media/Active-image44.png)
      
    - Within the file explorer in **Quick access** select **mslearn-knowledge-mining (1)** then click on **Select folder (2)**.

       ![](../media/ai-2.png)
      
    - If **Do you trust the authors of the files in this folder?** prompted click on **Yes, I trust the authors**.

         ![](../media/ai-15.png)

       > **Note**: If you are prompted to add required assets to build and debug, select **Not Now**.

### Task 2: Create Azure resources

To create the solution for Margie's Travel, you will need the following resources in your Azure subscription:

- An **Azure AI Search** resource that will manage indexing and querying.
- An **Azure AI Services** resource that provides AI services for skills that your search solution can use to enrich the data in the data source with AI-generated insights.
- A **Storage account** with a blob container in which the documents to be searched are stored.
  > **Important**: Your Azure AI Search and Azure AI Services resources must be in the same location.

#### Task 2.1: Create an Azure AI Search resource

In this task, you'll learn how to create an **Azure AI Search** resource in the Azure portal.

1. In a web browser, sign in to Azure portal using `https://portal.azure.com`.

1. Return to the Azure portal home page, and then click the **&#65291;Create a resource** button.

    ![](../media/Active-image21.png)
     
1. Search for and select **Azure AI Search** from the list on Create a resource page.

   ![](../media/Active-image22.png)

1. On the **Marketplace** page, select **Azure AI Search**.

   ![](../media/Active-image33.png)
    
1. On the **Azure AI Search** page, click on **Create**. 

   ![](../media/Active-image24.png)
   
1. Specify the following details to create an **Azure AI Search** service then click on **Next** untill you reach **Review + Create (6)** tab.
   
   | **Option**         | **Value**                                              |
   | ------------------ | -----------------------------------------------------  |
   | Subscription       | Leave default  **(1)**                                 |
   | Resource Group     | **ODL-GenAI-CL-XXXXXXX-01** **(2)**                |
   | Name               | *Enter a unique name* for your search service or use the format **searchservice-xxxxxx** (replace **xxxxxx** with the **Deployment ID** recorded in **Challenge 01**) **(3)** |
   | Location           | Use the same location as the resource group **(4)**           |
   | Pricing tier       | Basic   **(5)**                                               | 

    >**Note**: Here, xxxxxx refers to the deployment ID
    
    >**Note**: If you encounter the error **Cannot get costs for subscription**, please ignore it and proceed with the next step.
    
    >**Note**: If you face any issues while deploying the search service in selected region. please select different region to deploy the search service. 
    
    ![](../media/Active-image25.png)
   
1. Once validation is successful on the **Review + create** tab, click **Create** and wait for the deployment to complete then click on **Go to the resource**.

   ![](../media/Active-image26.png)

   ![](../media/Active-image27.png)

1. Review the **Overview** page on the blade for your Azure AI Search resource in the Azure portal. Here, you can use a visual interface to create, test, manage, and monitor the various components of a search solution, including data sources, indexes, indexers, and skillsets.

#### Task 2.2: Create an Azure AI Services resource

In this task, you'll learn how to create an Azure AI Search resource in the Azure portal. Your search solution will use this resource to enrich the data in the datastore with AI-generated insights.

1. Return to the Azure portal home page, and then click the **&#65291;Create a resource** button.

    ![](../media/Active-image21.png)
     
1. Search for and select **Azure AI Services (1) (2)** from the list then on the **Marketplace** page, select **Azure AI Services (3)**.

   ![](../media/Active-image28.png)

   ![](../media/Active-image29.png)
    
1. On the **Azure AI Services** page, click on **Create**. 

   ![](../media/Active-image30.png)
   
1. Specify the following details to create an **Azure AI Service** then click on **Review + Create (7)** tab.
   
   | **Option**         | **Value**                                              |
   | ------------------ | -----------------------------------------------------  |
   | Subscription       | Leave default  **(1)**                                 |
   | Resource Group     | **ODL-GenAI-CL-XXXXXXX-01**  **(2)**        |
   | Name               | *Enter a unique name* for your Azure AI Services or use the format **challengeservice-xxxxxx** (replace **xxxxxx** with the **Deployment ID** recorded in **Challenge 01**) **(3)** |
   | Location           | Use the same location as the resource group  **(4)**          |
   | Pricing tier       | Standard S0     **(5)**                                        |
   | By checking this box I acknowledge that I have read and understood all the terms below | Select the **Checkbox** **(6)**| 

    >**Note**: Here, xxxxxx refers to the deployment ID

    > **Note**: Ensure to use the same region as the Azure AI Search resource created previously.
    
      ![](../media/Active-image(31).png)
   
1. Once validation is successful on the **Review + create** tab, click **Create** and wait for the deployment to complete then click on **Go to the resource**.

#### Task 2.3: Create a storage account

In this task, you'll learn how to create a **Storage account** resource in the Azure portal, and in next steps will be creating blob container where the documents to be searched are stored.

1. On Azure Portal page, in Search resources, services and docs (G+/) box at the top of the portal, enter **Storage account** **(1)**, and then select **Storage account** **(2)** under services.

    ![](../media/Active-image34.png)

1. Click on **Create**.

    ![](../media/Active-image35.png)
   
1. Specify the following details to create an Azure **Storage account** then click on **Next** **(7)**  tab.
   
   | **Option**            | **Value**                                              |
   | ------------------    | -----------------------------------------------------  |
   | Subscription          | Leave default **(1)**                                  |
   | Resource Group        | **ODL-GenAI-CL-XXXXXXX-01** **(2)**         |
   | Storage account name  | *Enter a unique name* for your Storage account or use the format **storagexxxxxx** (replace **xxxxxx** with the **Deployment ID** recorded in **Challenge 01**) **(3)** |
   | Region                | Use the same location as the resource group **(4)**    |
   | Performance           | Standard **(5)**                                       |
   | Replication           | Locally redundant storage (LRS) **(6)**                | 

   ![](../media/strupdate.png)

1. On the **Advanced** tab, check the box next to **Allow enabling anonymous access on individual containers** and click on **Review + create**

   ![](../media/Active-image37.png)

1. Once validation is successful on  **Review + create**, click **Create** and wait for the deployment to complete click on **Go to resource**.
      ![](../media/Active-image38.png)
   
      ![](../media/Active-image39.png)
   
1. On the **Overview** page, note the **Subscription ID**; this identifies the subscription for which the storage account is provisioned.

   ![](../media/Active-image40.png)

    > **Tip**: Keep the **Storage Account** blade open; you will need the subscription ID and one of the keys in the next procedure.

### Task 3 and Task 4: Upload documents to Azure Storage and execute the uploaded script

In this task, you'll navigate between Visual Studio Code and the Azure portal to retrieve necessary credentials, update a batch file, and use the Azure CLI to upload documents to a blob container in your storage account.

>**Important**: Now that you have the required resources, you can upload some documents to your Azure Storage account.

1. Navigate back to Visual Studio Code, under the **Explorer** pane, expand the **labfiles** folder, then expand **01-azure-search (1)** and select **UploadDocs.cmd (2)**.

    ![](../media/ai-4.png)
   
1. Navigate back to browser tab displaying **Azure portal**, retrieve the **subscription ID (1)**, **Azure storage account name (2)**, and **Azure storage account key** by clicking **Show** > **Clipboard (3)** option from the recently created storage account and record the values in notepad.

      ![](../media/Active-image48.png)
   
      ![](../media/Active-image49.png)
   
1. Return to VS code and edit the batch file to replace placeholders **YOUR_SUBSCRIPTION_ID**, **YOUR_AZURE_STORAGE_ACCOUNT_NAME**, and **YOUR_AZURE_STORAGE_KEY** with the corresponding values which you recorded in previous step.

    ![](../media/ai-5.png)
   
1. Save your changes, and then right-click the **01-azure-search (1)** folder > **open an integrated terminal (2)**.

    ![](../media/ai-5.1.png)

1. Enter the following command to sign into your Azure subscription by using the Azure CLI:

   > **Note**: Ensure we have installed the Azure CLI and the Azure CLI Tools extension in Visual Studio Code.

   >**Note**: Make sure to replace <your-username> <your-password> with **Azure username** and **password** which you using from challenge-1.
   
    ```
    az login --username <your-username> --password <your-password>
    ```

    ![](../media/ai-6.png)
      
   > **Note**: If a web browser tab opens and prompts you to sign in to Azure, please sign in, then close the browser tab and return to Visual Studio Code.

1. Enter the following command to run the batch file. This will create a blob container in your storage account and upload the documents in the **data** folder to it.

    ```
    .\UploadDocs
    ```

   ![](../media/ai-7.png)

### Task 5: Data Import and Indexing:
#### Task 5.1: Index the documents

In this task, you'll learn how to create a search solution by indexing documents that are already in place. Navigating to your Azure AI Search resource in the Azure portal, configure the data source to utilize Azure Blob Storage, integrate cognitive skills for enrichment, customize the target index, and set up an indexer to process and index the documents effectively.

>**Note**: Now that you have the documents in place, you can create a search solution by indexing them.

1. In the Azure portal, browse to your **Azure AI Search** resource. Then, on its **Overview** page, select **Import data**.

   ![](../media/Active-image54.png)

1. On the **Connect to your data** page, in the **Data Source** list, select **Azure Blob Storage**. Then complete the data store details with the following values:
    
    - **Data Source**: Azure Blob Storage (1)
    - **Data source name**: margies-data  (2)
    - **Data to extract**: Content and metadata (3)
    - **Parsing mode**: Default (4)
    - **Subscription**: Leave default (5)  
    - **Connection string**: Select **Choose an existing connection (6)**. Then select your storage account (7), and finally select the **margies (8)** container that 
       was created by the UploadDocs.cmd script. then click on **Select (9)**.

        ![](../media/Active-image55.png)

        ![](../media/Active-image56.png)

        ![](../media/Active-image57.png)
      
    - **Managed identity authentication**: None (10)
    - **Container name**: margies (11)
    - **Blob folder**: *Leave this blank.* (12)
    - **Description**: Brochures and reviews in Margie's Travel web site. (13)
    - Click on **Add cognitive skills(Optional) (14)**

       ![](../media/Active-image58.png)

1. On **Add cognitive skills (Optional)** tab expand **Attach AI Services(1)**, within the section  select your **Azure AI Services (2)** resource.

     ![](../media/Active-image59.png)
   
1. Scroll down and expand **Add enrichments (1)** section and specify the following :
    
    - Change the **Skillset name** to **margies-skillset (2)**.
    - Select the checkbox for **Enable OCR and merge all text into merged_content field (3)**.
    - Ensure that the **Source data field** is set to **merged_content (4)**.
    - Leave the **Enrichment granularity level** as the **Source field (5)**, which sets the entire contents of the document being indexed, but note that you can change this to extract information at more granular levels, like pages or sentences.
  
      ![](../media/Active-image60.png)

    - Select the following enriched fields:

        | Cognitive Skill | Parameter | Field name |
        | --------------- | ---------- | ---------- |
        | Extract location names | | locations |
        | Extract key phrases | | keyphrases |
        | Detect language | | language |
        | Generate tags from images | | imageTags |
        | Generate captions from images | | imageCaption |

        ![](../media/Active-image61.png)
      
1. Double-check your selections (it can be difficult to change them later). Then proceed to the next step (*Customize target index*).

   ![](../media/Active-image62.png)
  
1. On **Customize target index** tab change the **Index name** to **margies-index (1)**.
   
1. Ensure that the **Key** is set to **metadata_storage_path (2)** and leave the **Suggester name** blank and **Search mode (3)** at its default value.

    ![](../media/Active-image63.png)
   
1. Make the following changes to the index fields, leaving all other fields with their default settings (**IMPORTANT**: you may need to scroll to the right to see the entire table):

    | Field name | Retrievable | Filterable | Sortable | Facetable | Searchable |
    | ---------- | ----------- | ---------- | -------- | --------- | ---------- |
    | metadata_storage_size | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | | |
    | metadata_storage_last_modified | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | | |
    | metadata_storage_name | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; |
    | metadata_author | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; |
    | locations | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | | | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; |
    | keyphrases | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | | | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; |
    | language | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&#10004; | | | |

    Use the below image to cross verify the option. 

     ![](../media/Active-image64.png)
   
1. Double-check your selections, paying particular attention to ensure that the correct **Retrievable**, **Filterable**, **Sortable**, **Facetable**, and **Searchable** options are selected for each field  (it can be difficult to change them later). Then proceed to the next step by clicking on **Next: Create an indexer**.

1. On the **Create an indexer** tab specify the following
      - Change the **Indexer name** to **margies-indexer (1)**.
      - Leave the **Schedule** set to **Once (2)**.
      - Expand the **Advanced options (3)** and ensure that the **Base-64 encode keys (4)** option is selected (generally, encoding keys make the index more efficient).
      
      - Select **Submit (5)** to create the data source, skillset, index, and indexer. The indexer is run automatically and runs the indexing pipeline, which:
          
          1. Extracts the document metadata fields and content from the data source.
          2. Runs the skillset of cognitive skills to generate additional enriched fields.
          3. Maps the extracted fields to the index.
      
             ![](../media/Active-image65.png)  

1. On **Azure AI Search** resource page, expand **Search management (1)** select **Indexers (2)** which should show the newly created **margies-indexer (3)**.

   ![](../media/Active-image66.png)  

1. Select **margies-indexer** . Wait a few minutes, and click **&orarr; Refresh** until the **Status** indicates success.

    ![](../media/Active-image67.png) 

#### Task 5.2: Search the index

In this task, you'll learn to search and query the index created earlier:

1. At the top of the **Overview** page for your Azure AI Search resource, select **Search explorer**.

    ![](../media/Active-image68.png)
   
1. In Search explorer, in the **Query string** box, enter `*` (a single asterisk), and then select **Search**.

    ![](../media/Active-image69.png)

   >**Note**: This query retrieves all documents in the index in JSON format. Examine the results and note the fields for each document, which contain document content, metadata, and enriched data extracted by the cognitive skills you selected.

1. In the **View** menu, select **JSON view**.

   ![](../media/Active-image70.png)

1. Note that the JSON request for the search is shown, like this:

    ```json
    {
      "search": "*"
    }
    ```
   ![](../media/Active-image71.png)
   
1. Modify the JSON request to include the **count** parameter, as shown here:

    ```json
    {
      "search": "*",
      "count": true
    }
    ```

1. Submit the modified search. This time, the results include a **@odata.count** field at the top of the results that indicates the number of documents returned by the search.

1. Try the following query:

    ```json
    {
      "search": "*",
      "count": true,
      "select": "metadata_storage_name,metadata_author,locations"
    }
    ```

    >**Note**: This time, the results include only the file name, author, and any locations mentioned in the document content. The file name and author are in the **metadata_storage_name** and **metadata_author** fields, which were extracted from the source document. The **locations** field was generated by a cognitive skill.

1. Now try the following query string:

    ```json
    {
      "search": "New York",
      "count": true,
      "select": "metadata_storage_name,keyphrases"
    }
    ```

    >**Note**: This search finds documents that mention "New York" in any of the searchable fields and returns the file name and key phrases in the document.

1. Let's try one more query:

    ```json
    {
      "search": "New York",
      "count": true,
      "select": "metadata_storage_name",
      "filter": "metadata_author eq 'Reviewer'"
    }
    ```

    >**Note**: This query returns the filename of any documents authored by *Reviewer* that mention "New York".

      ![](../media/newimg.png) 
  
### Task 6: Explore and modify the definitions of search components

The components of the search solution are based on JSON definitions, which you can view and edit in the Azure portal.

While you can use the portal to create and modify search solutions, it's often desirable to define the search objects in JSON and use the Azure AI Service REST interface to create and modify them.

#### Task 6.1: Get the endpoint and key for your Azure AI Search resource

In this task, you're preparing to execute CURL commands in Visual Studio Code to interact with Azure AI Service's REST interface:

1. In the Azure portal, return to the **Overview** page for your **Azure AI Search** resource, and in the top section of the page, find the **Url** for your resource (which looks like **https://resource_name.search.windows.net**) and copy it to the clipboard.

    ![](../media/Active-image72.png)

1. Expand **Settings**, select **Keys** and copy the **Primary admin key** to the clipboard.

    ![](../media/Active-image74.png)
   
1. In Visual Studio Code, in the Explorer pane, expand the **01-azure-search (1)** folder and its **modify-search (2)** subfolder, and select **modify-search.cmd (3)** to open it. You will use this script file to run *CURL* commands that submit JSON to the Azure AI Service REST interface.

     ![](../media/ai-16.png)
   
1. In **modify-search.cmd**, replace the **YOUR_SEARCH_URL** and **YOUR_ADMIN_KEY** placeholder with the URL and the key you copied to the clipboard and save the changes.

     ![](../media/ai-17.png)

    >**Note**: Don't run it yet!
   
#### Task 6.2: Review and modify the skillset

In this task, you will be configuring a skillset (skillset.json) in Visual Studio Code to integrate Azure AI Services with Azure AI Search:

1. In Visual Studio Code, in the **modify-search** folder, open **skillset.json**. This shows a JSON definition for **margies-skillset**.

      ![](../media/ai-18.png)
   
1. At the top of the skillset definition, note the **cognitiveServices** object, which is used to connect your Azure AI Services resource to the skillset.

1. In the Azure portal, search for Azure AI Services resource (<u>not</u> your Azure AI Search resource!)

      ![](../media/newaiservice.png)

1. From the left navigate to Azure AI **Multi-Service-Account** and select the **challengeservice**.

      ![](../media/newaiservice1.png)

1. On **Azure AI Multi-Services-Account** overview page, from the left navigation pane expand **Resource Management** select **Keys and Endpoints**. Then copy **Key 1** to the clipboard.

    ![](../media/Active-image79.png)
   
1. In Visual Studio Code, in **skillset.json**, replace the **YOUR_COGNITIVE_SERVICES_KEY** placeholder with the Azure AI Services key you copied to the clipboard.

   ![](../media/ai-19.png)
   
1. Scroll through the JSON file, noting that it includes definitions for the skills you created using the Azure AI Search user interface in the Azure portal. At the bottom of the list of skills, an additional skill has been added with the following definition:

    ```
      {
        "@odata.type": "#Microsoft.Skills.Text.V3.SentimentSkill",
        "name": "get-sentiment",
        "description": "New skill to evaluate sentiment",
        "context": "/document",
        "defaultLanguageCode": "en",
        "inputs": [
          {
            "name": "text",
            "source": "/document/merged_content"
          },
          {
            "name": "languageCode",
            "source": "/document/language"
          }
        ],
        "outputs": [
          {
            "name": "sentiment",
            "targetName": "sentimentLabel"
          }
        ]
      }
    ```

   >**Note**: The new skill is named **get-sentiment**, and for each **document** level in a document, it will evaluate the text found in the **merged_content** field of the document being indexed (which includes the source content as well as any text extracted from images in the content). It uses the extracted **language** of the document (with a default of English) and evaluates a label for the sentiment of the content. Values for the sentiment label can be "positive", "negative", "neutral", or "mixed". This label is then output as a new field named **sentimentLabel**.

1. Save the changes you've made to **skillset.json**.

#### Task 6.3 : Review and modify the index

In this task, you will review the modify-index.json file in Visual Studio Code which shows a JSON definition for **margies-index**

1. In Visual Studio Code, in the **modify-search (1)** folder, open **index.json (2)**. This shows a JSON definition for **margies-index**.

     ![](../media/ai-20.png)
   
1. Scroll through the index and view the field definitions. Some fields are based on metadata and content in the source document, and others are the results of skills in the skillset.
1. At the end of the list of fields that you defined in the Azure portal, note that two additional fields have been added:

    ```
    {
        "name": "sentiment",
        "type": "Edm.String",
        "facetable": false,
        "filterable": true,
        "retrievable": true,
        "sortable": true
    },
    {
        "name": "url",
        "type": "Edm.String",
        "facetable": false,
        "filterable": true,
        "retrievable": true,
        "searchable": false,
        "sortable": false
    }
    ```

1. The **sentiment** field will be used to add the output from the **get-sentiment** skill that was added to the skillset. The **url** field will be used to add the URL for each indexed document to the index, based on the **metadata_storage_path** value extracted from the data source. Note that the index already includes the **metadata_storage_path** field, but it's used as the index key and Base-64 encoded, making it efficient as a key but requiring client applications to decode it if they want to use the actual URL value as a field. Adding a second field for the unencoded value resolves this problem.

#### Task 6.4: Review and modify the indexer

In this task, you will review the **indexer.json** file in Visual Studio Code which shows a JSON definition for **margies-indexer**

1. In Visual Studio Code, in the **modify-search (1)** folder, open **indexer.json (2)**. This shows a JSON definition for **margies-indexer**, which maps fields extracted from document content and metadata (in the **fieldMappings** section) and values extracted by skills in the skillset (in the **outputFieldMappings** section) to fields in the index.

     ![](../media/ai-21.png)
    
1. In the **fieldMappings** list, note the mapping for the **metadata_storage_path** value to the base-64 encoded key field. This was created when you assigned the **metadata_storage_path** as the key and selected the option to encode the key in the Azure portal. Additionally, a new mapping explicitly maps the same value to the **url** field, but without the Base-64 encoding:

    ```
    {
        "sourceFieldName" : "metadata_storage_path",
        "targetFieldName" : "url"
    }
    
    ```

    > **Note**: All of the other metadata and content fields in the source document are implicitly mapped to fields of the same name in the index.

1. Review the **ouputFieldMappings** section, which maps outputs from the skills in the skillset to index fields. Most of these reflect the choices you made in the user interface, but the following mapping has been added to map the **sentimentLabel** value extracted by your sentiment skill to the **sentiment** field you added to the index:

    ```
    {
        "sourceFieldName": "/document/sentimentLabel",
        "targetFieldName": "sentiment"
    }
    ```

#### Task 6.5 : Use the REST API to update the search solution

In this task, you will update JSON definitions in Visual Studio Code for Azure AI Search to include new fields like sentiment analysis results and document URLs. Run modify-search.cmd to apply changes and start indexing. Monitor progress in Azure portal's Indexers section for completion and document size warnings during sentiment analysis.

1. Right-click the **modify-search** folder and select **open an integrated terminal**.

     ![](../media/ai-25.png)
   
1. In the terminal pane for the **modify-search** folder, enter the following command to run the **modify-search.cmd** script, which submits the JSON definitions to the REST interface and initiates the indexing.

    ```
    .\modify-search
    ```

1. When the script has finished, return to the **Overview** page for your **Azure AI Search** from the left navigation pane expand **Search management** and select **Indexers**. Then periodically select **Refresh** to track the progress of the indexing operation. It may take a minute or so to complete.

   ![](../media/Active-image84.png)

    >**Note**: There may be some warnings for a few documents that are too large to evaluate sentiment. Often, sentiment analysis is performed at the page or sentence level rather than the full document, but in this scenario, most of the documents, particularly the hotel reviews, are short enough for useful document-level sentiment scores to be evaluated.

#### Task 6.6 : Query the modified index
In this task, you'll perform a query in Azure AI Search to retrieve URLs, sentiment, and key phrases for documents mentioning "London" with positive sentiment, authored by "Reviewer".

1. At the top of the overview blade for your Azure AI Search resource, select **Search explorer**.
1. In Search explorer, in the **Query string** box, submit the following JSON query:

    ```json
    {
      "search": "London",
      "select": "url,sentiment,keyphrases",
      "filter": "metadata_author eq 'Reviewer' and sentiment eq 'positive'"
    }
    ```

   ![](../media/newaiservice2.png)

    This query retrieves the **url**, **sentiment**, and **keyphrases** for all documents that mention *London* authored by *Reviewer* that has a positive **sentiment** label (in other words, positive reviews that mention London).

1. Close the **Search explorer** page to return to the **Overview** page.

### Task 7: Create a search client application

Now that you have a useful index, you can use it from a client application. You can do this by consuming the REST interface, submitting requests, and receiving responses in JSON format over HTTP, or you can use the software development kit (SDK) for your preferred programming language. In this exercise, we'll use the SDK.

> **Note**: You can choose to use the SDK for either **C#** or **Python**. In the steps below, perform the actions appropriate for your preferred language.

#### Task 7.1 : Get the endpoint and keys for your search resource

In this task, you'll retrieve the endpoint URL and keys for your Azure AI Search resource from the Azure portal, essential for managing and querying your search resources in upcoming tasks.

1. In the Azure portal, navigate back to **Azure AI Search**. On the Overview page for the **Azure AI Search** resource, note the url value, which should be similar to **https://your_resource_name.search.windows.net**. Please record this value in Notepad as it will be required in upcoming tasks.

    ![](../media/Active-image86.png)
   
1. From the left navigation expand **Settings** select **Keys**, note that there are two **admin** keys and a single **Manage query keys** key.

   >**Note**: An *admin* key is used to create and manage search resources
   >**Note**: An *Manage query keys* key is used by client applications that only need to perform search queries.

    ![](../media/Active-image87.png)

1.  Please copy the **Manage query keys** to the clipboard and record it in Notepad, as it will be needed for upcoming tasks.

     ![](../media/Active-image88.png)
    
#### Task 7.2 : Prepare to use the Azure AI Search SDK

In this task, you'll prepare your development environment in Visual Studio Code to integrate with Azure AI Search SDK by installing the necessary packages (Azure.Search.Documents for C# or azure-search-documents for Python) and configuring endpoint URL and query key in the respective configuration files.

1. In Visual Studio Code, in the **Explorer** pane, browse to the **01-azure-search** folder and expand the **C-Sharp** or **Python** folder depending on your language preference.
1. Right-click the **margies-travel** folder and open an integrated terminal. Then install the Azure AI Search SDK package by running the appropriate command for your language preference:
   > **Note**: Please ensure the necessary extensions are already installed in the VS Code.

    **C#**
    
    ```
    dotnet add package Azure.Search.Documents --version 11.1.1
    ```
    **Python**
    
    ```
    pip install azure-search-documents==11.0.0
    ```
    
1. View the contents of the **margies-travel** folder, and note that it contains a file for configuration settings:
    - **C#**: appsettings.json
    - **Python**: .env

1. Open the configuration file and update the **YOUR_SEARCH_ENDPOINT**  with the **Azure AI Search** *Endpoint URL* link and  **YOUR_SEARCH_QUERY_KEY** values with **Manage query keys** which you recorded in previous tasks and save the changes.

    - **C#**: appsettings.json

       ![](../media/ai-22.png)

    - **Python**: .env
  
      ![](../media/ai-23.png)

#### Task 7.3 : Explore code to search an index

In this task, you'll explore the code for a web application (C# ASP.NET Razor or Python Flask) within the margies-travel folder. You'll review how it interacts with Azure AI Search SDK to perform search queries, configure search clients, and manage search results, including filtering, sorting, and highlighting content fields.

The **margies-travel** folder contains code files for a web application (a Microsoft C# *ASP.NET Razor* web application or a Python *Flask* application), which includes search functionality.

1. Open the following code file in the web application, depending on your choice of programming language:
    - **C#**:Pages/Index.cshtml.cs
    - **Python**: app.py

1. Near the top of the code file, find the comment **Import search namespaces**, and note the namespaces that have been imported to work with the Azure AI Search SDK:

1. In the **search_query** function, find the comment **Create a search client**, and note that the code creates a **SearchClient** object using the endpoint and query key for your Azure AI Search resource:
   
1. In the **search_query** function, find the comment **Submit search query** and review the code to submit a search for the specified text with the following options:
    - A *search mode* that requires **all** of the individual words in the search text to be found.
    - The total number of documents found by the search is included in the results.
    - The results are filtered to include only documents that match the provided filter expression.
    - The results are sorted into the specified sort order.
    - Each discrete value of the **metadata_author** field is returned as a *facet* that can be used to display pre-defined values for filtering.
    - Up to three extracts of the **merged_content** and **imageCaption** fields with the search terms highlighted are included in the results.
    - The results include only the fields specified.

#### Task 7.4 : Explore code to render search results

In this task, you'll delve into the web application's code (either C# ASP.NET Razor or Python Flask) to understand how it presents search results:

The web app already includes code to process and render the search results.

1. Open the following code file in the web application, depending on your choice of programming language:
    - **C#**:Pages/Index.cshtml
    - **Python**: templates/search.html
1. Examine the code, which renders the page on which the search results are displayed. Observe that:
    - The page begins with a search form that the user can use to submit a new search (in the Python version of the application, this form is defined in the **base.html** template), which is referenced at the beginning of the page.
    - A second form is then rendered, enabling the user to refine the search results. The code for this form:
        - Retrieves and displays the count of documents from the search results.
        - Retrieves the facet values for the **metadata_author** field and displays them as an option list for filtering.
        - Creates a drop-down list of sort options for the results.
    - The code then iterates through the search results, rendering each result as follows:
        - Display the **metadata_storage_name** (file name) field as a link to the address in the **url** field.
        - Displaying *highlights* for search terms found in the **merged_content** and **imageCaption** fields to help show the search terms in context.
        - Display the **metadata_author**, **metadata_storage_size**, **metadata_storage_last_modified**, and **language** fields.
        - Display the **sentiment** label for the document. Can be positive, negative, neutral, or mixed.
        - Display the first five **keyphrases** (if any).
        - Display the first five **locations** (if any).
        - Display the first five **imageTags** (if any).

#### Task 7.5 : Run the web app

In this task, you'll be running the Margie's Travel web application locally, searching for specific terms like "London hotel" and "quiet hotel in New York", refining search results using filters and sorting options based on sentiment, observing keyword and location identification in documents.


 1. Return to the integrated terminal for the **margies-travel** folder and enter the following command to run the program:
    
    **C#**
    
    ```
    dotnet run
    ```
    > **Note:** If the command fails, click on the provided link in the error message to download the latest version of the Microsoft ASP.NET Core Shared Framework. After that, download and install .NET Core, and then run the command again.
        
    **Python**
     
    ```
    pip install flask
    flask run
    ```
    > **Note:** If the command fails, run **pip install python-dotenv** command and then run the command again.

1. Open the another tab in edge browse following the link (*http://localhost:5000/* or *http://127.0.0.1:5000/*) to open the **Margie's Travel** site in a web browser.

    ![](../media/Active-image101.png)
   
1. On the **Margie's Travel** website, enter **London hotel (1)** into the search box and click **Search (2)**.

    ![](../media/Active-image95.png)
   
1. Review the search results. They include the file name (with a hyperlink to the file URL), an extract of the file content with the search terms (*London* and *hotel*) emphasized, and other attributes of the file from the index fields.

    ![](../media/Active-image96.png)
   
1. Observe that the results page includes some user interface elements that enable you to refine the results. These include:
    
    - A *Filter by author* based on a facet value for the **metadata_author** field. This demonstrates how you can use *facetable* fields to return a list of *facets* - fields with a small set of discrete values that can be displayed as potential filter values in the user interface.
    
    - A **Sort by** ability to *order* the results based on a specified field and sort direction (ascending or descending). The default order is based on *relevancy*, which is calculated as a **search.score()** value based on  a *scoring profile* that evaluates the frequency and importance of search terms in the index fields.

1. Select the **Reviewer** filter and the **Positive to negative** sort option, and then select **Refine Results**.

    ![](../media/Active-image97.png)
   
1. Observe that the results are filtered to include only reviews and sorted based on the sentiment label.
   
    ![](../media/Active-image98.png)
   
1. On the **Margie's Travel** website, enter **quiet hotel in New York (1)** into the search box and click **Search (2)**.

    ![](../media/Active-image99.png)
   
1. Try the following search terms:
    - **Tower of London** (observe that this term is identified as a *key phrase* in some documents).
    - **skyscraper** (observe that this word doesn't appear in the actual content of any documents but is found in the *image captions* and *image tags* that were generated for images in some documents).
    - **Mojave desert** (observe that this term is identified as a *location* in some documents).

1. Close the browser tab containing Margie's Travel website and return to Visual Studio Code. Then, in the Python terminal for the **margies-travel** folder (where the dotnet or flask application is running), enter Ctrl+C to stop the app.


## Success criteria:


To successfully complete this challenge, you must:

   - Deploy the Azure Search Service and Azure Storage Account.
   - Add data to the storage account.
   - Index the documents in Azure AI Search using the Azure portal.
   - Customize the index and configure the indexer in Azure AI Search.
   - Modify and explore search components using JSON definitions.
   - Utilize the Azure AI Search SDK to create a client application for search.
   - Run the web application locally, perform searches, and refine search results effectively.


## Additional Resources:

- Refer to [What is Azure AI Search](https://learn.microsoft.com/en-us/azure/search/search-what-is-azure-search) for reference.
- [What are Indexes in Azure AI Search?](https://learn.microsoft.com/en-us/azure/search/search-what-is-an-index)
- [Searching document text at scale using Azure Cognitive Search](https://benalexkeen.com/searching-document-text-at-scale-using-azure-cognitive-search/)

To learn more about Azure AI Search, see the [Azure AI Search documentation](https://docs.microsoft.com/azure/search/search-what-is-azure-search).

## Proceed with the next Challenge by clicking on **Next**>>.

# Challenge 03: Deploy NVIDIA NIM on Azure

### Estimated Time: 120 minutes

## Introduction

This lab guides participants through deploying NVIDIA NeMo Inference Manager (NIM) on Azure, which facilitates rapid development and deployment of sophisticated AI models for various applications. NVIDIA NIM is a model deployment and management solution that enables efficient utilization of NVIDIA GPUs for AI model inference. This deployment involves using Azure's powerful cloud infrastructure to host NIM containers, which simplifies the integration of AI models into production environments by managing model lifecycle, deployment, and scaling in Azure Machine Learning (AML) services.

Participants will begin by creating an NVIDIA account to generate an API key, essential for accessing NVIDIA’s NGC resources, such as container images for NeMo models. Then, the lab covers setting up Azure Container Registry (ACR) for storing these images, configuring Git Bash to interact with Azure, and updating relevant configuration files within Visual Studio Code. After this setup, participants will deploy the NIM container through Azure Machine Learning, which will handle the GPU-based model deployment and expose it through a managed online endpoint.

## Solution Guide

## Task 1: Generate NGC API KEY

> **Note:** This process of getting the NGC API key is no longer recommended. The participant is recommended to get the API key through build.nvidia.com as mentioned on the Scenario page.

The NVIDIA API key is a unique identifier used to authenticate requests to NVIDIA's APIs, such as the NGC (NVIDIA GPU Cloud) services. This key allows developers to access various resources, including pre-trained models, GPU-accelerated software, and container images. Obtaining an API key typically involves creating an account on NVIDIA's developer portal and generating the key within the account settings. It is important to keep this key secure, as it grants access to your NVIDIA resources and can be used for billing purposes.

1. **Go to [build.nvidia.com](https://build.nvidia.com)**

1. **Login or Create an Account**:
Click on the **Login** button in the top-right corner to create a new account. Enter your organization email to receive free credits to use NVIDIA NIM and click **Next**.

   ![build.nvidia.com](../media/nvaie-1.png)

   >**Note**: We recommend using your Email to log in, as this will provide you with 1,000 free credits. Alternatively, you can use the Username and Password available in the Environment tab to create an account; however, this option does not include free credits.

1. **Create Your NVIDIA Account**:
You will be redirected to a page where you can create your NVIDIA account. Provide your **Personal email address** **(1)** and then click on **Create (2)**.This account is required to download NIMs and start using them in your Azure platform.

   ![](../media/i-13.png)

1. On the **Create your Account**, page providr thre following details and then click on **Create account (6)**.  

   - Email: Provide your **Personal email address (1)**
   - Password: Provide your **Password (2)**
   - Confirm password: Enter your password again **(3)**
   - Stay logged in: Check the box **(4)**
   - Enable **I am human** check box **(5)**

     >**Note:** You may be asked to choose the pictures. If requested, please complete and verify.

   ![](../media/i-14.png)

1. **Verify Your Email Address**:
Log into your **email** and you will get a verification code to your email to complete the verification process.

1. Enter the **code (1)** and click on **Continue (2)**.

   ![](../media/i15.png)

1. **Privacy Settings**:
Once verification is complete, you'll be redirected to a page with privacy-related questions. Choose your privacy settings and click **Submit**.

   ![](../media/nvaie-5.png)

1. **Create Your NGC (NVIDIA GPU Cloud) Account**:
In the next step, create your NGC account by providing your NVIDIA cloud account name. Provide any name for Account name and click on **Create NVDIA Cloud Account**.

   ![](../media/nvaie-6.png)

### Success!

You have successfully created your NVIDIA NVAIE and NVIDIA Cloud accounts. Verify that you are provided with free 1000 credits to try out NIMs.

   ![](../media/nvaie-credits.png)

### Explore NIMs:

- Now you can explore all available NIMs! Use the search bar at the top to search for any model or LLM task (e.g., search for "Llama" or "Retrieval").
- Explore the search results, open the NIM of interest, and experiment with it.
- You are provided with **1000 free credits**, each translating into one API call. Therefore, you have **1000 API calls** to try out the NIMs.

   ![](../media/nvaie-7.png)
  
- You can also call these NIMs in your Python application using the OpenAI library (refer to the Python code on the right) or using [NVIDIA LangChain endpoints](https://python.langchain.com/docs/integrations/chat/nvidia_ai_endpoints/).

   ![](../media/nvaie-8.png)

### Generate API Key

1. Now log in to [nvidia](https://ngc.nvidia.com/signin) account using your credentials to proceed. 

1. Enter your **Email address (1)** and click on **Continue (2)**.

   ![](../media/i-16.png)

1. On the **Set Your Profile** page, fill in your details and click **Submit**.

   ![](../media/i17.png)

1. If you receive a pop-up for **Set Email Preferences For Your Services**, simply click on **Close**.

   ![](../media/nvidia10.png)

1. Once your account is created or you've successfully logged in.

1. You will see a pop-up. On the **Set Email Preferences For Your Services** page, you can either **close** it or click **Set Email Preferences** to receive updates regarding security, announcements, and maintenance for all your services.

   ![](../media/nv8.png)

1. In the search bar, look for **Llama-3.1-8b-instruct**.

   ![](../media/nv7.png)

1. Scroll down and select **Llama-3.1-8b-instruct**. 

   ![](../media/nv6.png)

1. On the left-hand side, click **Get Container**.

   ![](../media/nv5.png)

1. A pop-up will appear on the **Approval Required** page. Click **Join** for the **NVIDIA Developer Program**, and it will redirect you to the NVIDIA Developer Portal.

   ![](../media/nv4.png)

1. On the **NVIDIA Developer Portal**, under **Integrate NIM into your application**, provide the necessary details (you can also provide random details) and click **Join**.

   ![](../media/nv3.png)

1. Navigate back to your **NVIDIA Account**. Select  **Organization**.

   ![](../media/i19.png)

1. click **Subscriptions (1)** on the left. Here, you will see the **Active (2)** status for the NVIDIA Developer Program.

   ![](../media/i20.png)

    >**Note**: Click on **Close**, if **Set Email Preferences For Your Services** pop up appears. 

1. Click on **Account** at the top of the page and navigate to the **Setup** section.

   ![](../media/nvidia4.png)

1. Click on **Generate API Key** to create a new key for accessing the necessary services.

   ![](../media/nvidia5.png)

1. From the top, click on **+ Generate API Key** to create a new API key.

   ![](../media/nvidia8.png)

1. Click on **Confirm** to generate your new API key.

   ![](../media/nvidia9.png)

1. Carefully copy and paste your generated **API key** in a notepad, essential for accessing various services and features paste the API key in the notebook. Ensure you store it securely, as it may not be displayed again after you leave the page.

   ![](../media/nvidia7.png)

## Accessing the Azure portal

>**Important**: You can find the Username and Password within the environment by navigating to the **Environment** **(1)** tab in the left pane then copy the **Azure Username** **(2)** and **Azure Password** **(3)**, which will be required for signing into the Azure portal in later steps and you can record the **Deployment Id** **(4)**, which can be used to provide a unique name to the resources during deployment.

   >**Note**: Numbers and ID's values may vary kindly ignore values in screenshots and copy values from **Environment** tab.

 ![](../media/Active-image19.png)
 ![](../media/Active-image(20).png)

1. To access the Azure portal, within labvm open **Microsoft Edge** and browser to the [Azure Portal](https://portal.azure.com/).

1. On the **Sign into Microsoft Azure tab**, you will see a login screen. Enter the following email/username, and then click on **Next**.
   
   - **Email/Username:** <inject key="AzureAdUserEmail"></inject>

     ![](../media/Active-image1.png)

1. Now enter the following password and click on **Sign in**.

   - **Password:** <inject key="AzureAdUserPassword"></inject>

      ![](../media/Active-image2.png)

1. When **Action Required** window pop up click on **Ask Later**.

    ![](../media/Active-image3.png)
   
1. If you see the pop-up **Stay Signed in?**, click **No**.

    ![](../media/Active-image4.png)

1. If a **Welcome to Microsoft Azure** pop-up window appears, click **Cancel** to skip the tour.

    ![](../media/Active-image5.png)

### Docker Start

1. Double click on the Docker Desktop Shortcut on the screen.

1. Click on **Accept**(1) on the Docker Subscription Service Agreement.

   ![](../media/nvdocker1.png)

1. Select Use recommended setting(requires administrator password) and click on **Finish**(1).

   ![](../media/nvdocker2.png)

1. Click **Skip**(1) on the Welcome to docker page.

   ![](../media/nvdocker3.png)

1. Click **Skip** on the Welcome Survey page.

   ![](../media/nvdocker4.png)

1. Click **Skip** on the Sign in page.

   ![](../media/nvdocker5.png)

1. Minimize Docker Desktop and continue with next steps.

   ![](../media/nvdocker6.png)

   >**Note:** If you encounter an error such as **"Docker Desktop - Unexpected WSL error"**, click **Quit** to close Docker and follow below steps:

   ![](../media/nvdocker7.png)

   - Search for the PowerShell in your lab-VM, right-click on the PowerShell, and select run as administrator.
     
     ![](../media/powershell.png)
     
   - Run the below command:
      ```
      #Check if 'docker-users' group exists before adding to 'Administrators'
       $dockerUsersGroupExists = Get-LocalGroup -Name 'docker-users' -ErrorAction SilentlyContinue
       $CurrentUser = "demouser"
       if ($dockerUsersGroupExists -ne $null) {
           Add-LocalGroupMember -Group 'docker-users' -Member $CurrentUser -Verbose
           Write-Host "User '$CurrentUser' added to the 'docker-users' group."
       } else {
           Write-Host "'docker-users' group does not exist. Skipping adding the user to 'docker-users'."
     
        }
       ```
   - Once the command is executed, from the resources tab restart the Virtual machine.

     ![](../media/res.png)
  
   - Once the VM is restarted, Reopen the **Docker Desktop**.

### Task 2: Create Container Registry

Azure Container Registry (ACR) is a managed Docker container registry service that allows you to store and manage private Docker container images and artifacts in Azure. It provides a secure and scalable solution for building, deploying, and managing containerized applications, enabling seamless integration with Azure services.

1. In the search bar of the Azure portal, type **Container registries** (1). From the search results, select **Container registries** (2) to access the container registry management section.

   ![](../media/cr1.png)

1. Click on **+ Create**.

1. On the **Basics** tab of Create **Container Registry**, provide details as mentioned in the table below and select **Review + create** (5) at the bottom of the page and subsequently click on **Create**.

    | Setting | Action |
    | -- | -- |
    | **Subscription** | Default |
    | **Resource Group** | **ODL-GenAI-CL-XXXXXX-01** (1) |
    | **Registry name** | **amlregistry<inject key="DeploymentID" enableCopy="false"/>** (2) |
    | **Location** | **East US 2** (Choose the same location where the resource group) (3) |
    | **Pricing plan** | **Standard** (4) |

   > **Note**: Unique ID (XXXXXX) refers to DeploymentID.

   ![](../media/aml1.png)

   ![](../media/aml2.png)

1. Once the deployment is completed, click on **Go to resource**.

1. From the Overview page copy the subscription ID and paste the  subscription ID into the notebook you will use later use.

   ![](../media/aml3.png)

### Task 3: Setup Git Bash Environment

1. In the **LabVM**, click on the Start menu and search for **Git Bash** **(1)**. Once you find it, right-click on **Git Bash** **(2)** and select **Run as Administrator** **(3)** to launch Git Bash with elevated privileges.

   ![](../media/git-bash-run.png)

1. Run the following command, This command downloads the latest version of jq, a lightweight and flexible command-line JSON processor, and saves it as an executable file named `jq.exe` in the `/usr/bin/` directory, making it accessible for command-line use.

   ```
   curl -L -o /usr/bin/jq.exe https://github.com/stedolan/jq/releases/latest/download/jq-win64.exe
   ```

1. Install the az CLI by navigating to the below link:

      ```
      $ProgressPreference = 'SilentlyContinue'; Invoke-WebRequest -Uri https://azcliprod.blob.core.windows.net/msi/azure-cli-2.51.0.msi -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'; Remove-Item .\AzureCLI.msi
      ```

1. Now, install the ml extension

   ```
   az extension add -n ml
   ```

   ```
   az extension update -n ml
   ```

1. Run the help command to verify your installation and see available subcommands:

   ```
   az ml -h
   ```

1. Clone the GitHub repository to your Desktop 

   ```
   cd Desktop
   ```

   ```
   git clone https://github.com/CloudLabsAI-Azure/nim-deploy.git
   ```

1. Use the command below to navigate to the directory:

   ```
   cd nim-deploy/cloud-service-providers/azure/azureml/cli
   ```

Detailed instructions can be found [here](https://github.com/NVIDIA/nim-deploy/tree/main/cloud-service-providers/azure/azureml/cli).

### Task 4: Visual Studio config.sh file update

1. Start **Visual Studio Code** by launching it from your desktop.

   ![](../media/vscode1.png)

1. Go to the **Explorer** panel in the upper left corner, click on **Open Folder**,  select **cli folder** from the location where you have cloned the repo in previous step `Desktop/cloud-service-providers/azure/azureml/cli` , and then click on **Select Folder** to open it in Visual Studio Code.

   ```
   Desktop\nim-deploy\cloud-service-providers\azure\azureml\cli
   ```

   ![](../media/vscode2.png)

1. Select **Yes, I trust the authors**.

   ![](../media/vscode3.png)

1. Open the `config.sh` file and update the values as needed. You can refer to the `example_config.sh` file for guidance on the appropriate configurations and settings.

    | Setting | Action |
    | -- | -- |
    | **subscription_id** | **<inject key="SubscriptionID" enableCopy="false"/>** |
    | **resource_group** | **ODL-GenAI-CL-XXXXXXX-01**  |
    | **workspace** | **ml-workspace{suffix}** (Provide the name of the workspace you want to create) |
    | **location** | **EastUS2**, **CentralUS** (Choose the same location where the resource group is and make sure there is no space between the location name) |
    | **ngc_api_key** | Provide the NGC key  |
    | **email_address** | Enter the email from the Environmental Details tab  |
    | **acr_registry_name** | **amlregistry{suffix}** |
    | **image_name** | **nim-meta-llama-3.1-8b-instruct:latest**|
    | **endpoint_name** | **llama-3-1-8b-nim-endpoint{suffix}** |
    | **deployment_name** | **llama3-1-8b-nim-dep{suffix}** |

   ![](../media/vscode4.png)

   ![](../media/up2.png)

   > **Note** : Replace `{suffix}` with the Deployment ID. Navigate to **Environment** **(1)**, and copy the **Deployment ID** from the **User Name** field.

   ![](../media/a26.png)

1. Press **Ctrl + S** to save the changes you made to the file.

## Task 5: Create AzureML Deployment of the NIM Container

### Login to Azure with Your Credentials

1. Switch back to the Git Bash terminal.

1. Update your login credentials (**Username** and **Password**) and set the **subscription_id** for your subscription.
   
   - **Subscription Id:** - <inject key="SubscriptionID"></inject>
   - **Username:** <inject key="AzureAdUserEmail"></inject>
   - **Password:** <inject key="AzureAdUserPassword"></inject>

      ```
      source config.sh
      ```
      ```
      az login --user <Username> --password <Password>
      az account set -s ${subscription_id}
      ```
      > **Note:** If you encounter any issues during login, you can execute the following command.

      ```
      az account clear
      az config set core.enable_broker_on_windows=false
      az login --user <Username> --password <Password>
      az account set -s ${subscription_id}
      ```

1. This will prompt an Azure login window; please select your credentials to log in.

###  Task 6: Setup AzureML Workspace

1. Execute the following command to create a new AzureML workspace with the "Azure ML Secrets Reader" role assignment.

   ```cmd
    ./1_set_credentials.sh --create_new_workspace
   ```
   > **Note:** The above command creates a new workspace with the workspace name provided in the config.sh file.

1. You can find the newly created worksapce in azure

   ![](../media/u1.png)

###  Task 7: Store NGC API Key for Use in the AzureML Deployment

1. To Store NGC API Key for Use in the AzureML Deployment.You have two options for storing the NGC API Key:

   >**Note :** The NGC API Key needs to be stored within Azure so the AzureML workspace can access it during deployment. The API key is required to pull the correct model from the NGC model  catalog. The key can be provided as a workspace connection to the AzureML workspace.
   
   **Store the Key as a Workspace Connection:**
   Store the NGC API Key as a custom credential using a workspace connection.

   This script stores the NGC API Key as a workspace connection credential and verifies if the provided workspace can access it.

   Run the following script to configure this and verify the connection

   ```cmd
    ./2_provide_ngc_connection.sh
   ```

###  Task 8: Save NIM Container in Your Container Registry

Pull the NIM Docker container for the model specified in the `config.sh` file. Create another Docker container wrapped around the NIM container for deployment in AzureML and push this new container to an Azure container registry that can be accessed by your AzureML endpoint. All required commands are provided in the `3_save_nim_container.sh` script.

1. Run the following command to **save the NIM container in your container registry**.

   ```cmd
   ./3_save_nim_container.sh
   ```
   >**Note:** This action will approximately take around 20-25 Minutes.

1. Navigate to your container registry (**amlregistry**) , Under the service click on the Respositiories select your **nim-meta-llama-3.1-8b-instruct** regiestry, here you will find your image is pushed with the tag name **latest**.

   ![](../media/bash2.png)

###  Task 9: Create Managed Online Endpoint

1. Run the following command to **create a managed online endpoint**.

   ```cmd
   ./4_create_endpoint.sh
   ```

   >**Note :** This command creates an endpoint with the name provided in the config.sh file.
   > **Note :** If you see an `ERROR: 'ml' is misspelled or not recognized by the system.` Run the below commands to remove, install and verify ml extension.

   ```
   az extension remove -n ml
   ```

   ```
   az extension add -n ml
   ```

   ```
   az ml -h
   ```

   >**Note :** Rerun the command to create endpoint.

###  Task 10: Role Assignment

1. Go to **amlregistry** container regiestry first. navigate to **Access control (IAM)** (1). Click on **+ Add**(2) and choose **Add role assignment** (3). This allows you to assign specific roles to users, groups, or applications, controlling their permissions to manage resources associated with the app service.

   ![](../media/bash3.png)

1. In the **Add role assignment** page, under the Role tab, choose **Job function roles** (1). Search and select **AcrPull** (2) within this category, and then click **Next** (3) to proceed.

   ![](../media/bash4.png)

1. Next, under the **Members** tab, select **Managed identity** (1) for Assign access to, and then click on **+ Select members** (2). Further, under the **Select managed identities** on the right, choose **Machine learning online endpoint** (3) for **Managed identity**. Finally, under **Selected members**, choose the **llama3-1-8b-nim-endpoint-aml-1** (4), of choice and then continue by clicking on **Select** (5) and **Next** (6).

   ![](../media/bash5.png)

1. Click on **Review + assign**.

### Task 11: Create AzureML Deployment of the NIM Container

Create an AzureML deployment with the NIM container obtained from the provided Azure container registry.

1. Run the following command to **create AzureML deployment of the NIM container**.

   ```cmd
   ./5_create_deployment.sh
   ```

   >**Note:** This action will approximately take around 20-25 Minutes.

### Task 12: Verify Your Connection

1. Return to the **Azure Portal**.

2. Open the **ml-workspace** and click on **Launch studio**.

   ![](../media/nvverify1.png)

3. This will take you to **AML Studio**. From the left-hand menu, select **Endpoints** and choose your endpoint.

   ![](../media/nvverify2.png)

4. Go to the **Consume** tab, then copy the **REST endpoint** and **Primary key**.

   ![](../media/nvverify3.png)

5. In VS Code, open the **`test_chat_completions.sh`** file. Replace the following headers `<your-azureml-endpoint>`, `<your-azureml-endpoint-token>`, and `<deployment-name>` with the appropriate values. Ensure the **deployment-name** matches the one in your `config.sh` file and save the file.

   >**Note:** Ensure to add **/v1/chat/completions** towards the end of the endpoint.

6. Once you have updated all the headers, the code should look similar to the following:

   ```
   #!/bin/bash
   curl -X 'POST' \
     'https://llama-3-1-8b-nim-endpoint-aml-1.eastus2.inference.ml.azure.com/v1/chat/completions' \
     -H 'accept: application/json' \
     -H 'azureml-model-deployment: llama3-1-8b-nim-deployment-aml-1' \
     -H 'Authorization: Bearer 3L3s8qb6dCQq7TTgorFnwDVZT8qsvId5' \
     -H 'Content-Type: application/json' \
     -d '{
     "messages": [
       {
         "content": "You are a polite and respectful chatbot helping people plan a vacation.",
         "role": "system"
       },
       {
         "content": "What should I do for a 4 day vacation in Spain?",
         "role": "user"
       }
     ],
     "model": "meta/llama-3.1-8b-instruct",
     "max_tokens": 500,
     "top_p": 1,
     "n": 1,
     "stream": false,
     "stop": "\n",
     "frequency_penalty": 0.0
   }'
   
   ```

1. Run the following command to Verify Connection.

   ```
   ./test_chat_completions.sh
   ```

1. You will see the output similar to the below screenshot.

   ![](../media/llama-output.png)

# Challenge 04:  Deploy an AI-Powered Chat App 

### Estimated Time: 90 minutes

### Introduction:

In this challenge, you'll deploy an AI-powered chat application specifically designed for Contoso Electronics. This app, built with React for the frontend and Python for the backend, showcases advanced features like chat and Q&A interfaces, all augmented by AI capabilities. It's an excellent opportunity for you to explore the integration of Azure OpenAI Service with the GPT-3.5 Turbo model and Azure Cognitive Search for efficient data indexing and retrieval.

This sample app is more than just a chat interface; it demonstrates the Retrieval-Augmented Generation pattern, offering a rich, ChatGPT-like experience over Contoso's own data. The app's features include trustworthiness evaluation of responses with citations, tracking of source content, data preparation, prompt construction, and orchestrating interaction between the ChatGPT model and Cognitive Search. You'll also find adjustable settings in the UX for experimentation and optional performance tracing and monitoring with Application Insights.

In this challenge, your task is to deploy this comprehensive chat solution for Contoso, allowing them to evaluate its capabilities and integrate it into their environment. The repository comes with sample data, representing a ready-to-use, end-to-end solution. This app is a valuable tool for Contoso's employees to inquire about company benefits, internal policies, job descriptions, and roles.

You will be using Terraform to deploy the chat app. 

The chat application integrates seamlessly with different Azure services to provide an intelligent user experience. Here's a simple overview of each service used by the app:

- **App Service:** This hosts the chat app, ensuring it can respond to the prompts sent by users from the uploaded relatable data.
- **Application Insights:** It proactively monitors the app's performance, taking care of issues before they become significant.
- **Document Intelligence:** Using AI, it understands the content in uploaded documents, making user information more insightful.
- **Azure OpenAI:** Enhances the app's capabilities with natural language understanding and responses.
- **Shared Dashboard:** Acts as a central hub for team collaboration and data sharing.
- **Smart Detector Alert Rule:** Monitors the app's health and notifies the team if any issues arise.
- **Search Service:** Empowers users with dynamic and efficient search functionality within the app.
- **Log Analytics Workspace:** Tracks and analyzes app activity, offering valuable insights and logs.
- **App Service Plan:** Optimizes resource allocation for optimal app performance.
- **Storage Account:** Securely stores the data that will be used by the Azure AI Search service to provide the inputs to the chat app.

Together, these services create a responsive chat application that combines AI features, monitoring capabilities, and efficient data management, providing Contoso with an exceptional user experience.

## Architecture diagram:

![](../media/Active-image258.png)

## Solution Guide:

## Prerequisite
   
1. Start Powershell 7 +.
   
2. Ensure you run `pwsh.exe` from a PowerShell terminal. If this fails, you likely need to upgrade PowerShell.

## Task 1: Deploy the  AI-Powered Chat App.

In this task, you'll learn the process of Deploying the Infrastructure.

1. In the **LabVM**, in the Windows Search bar type **Powershell** and select **PowerShell 7-preview (x64)** then **Run as Administrator**.

    ![](../media/Active-image102.png)

      > Note: If you are not able to see the Powershell 7-preview. please do run the below commands line by line in Powershell ISE to install the Powershell 7-preview.

   ```
   $PSVersionTable.PSVersion
   
   # Define the URL for the latest PowerShell 7 Preview MSI installer
   $url = "https://github.com/PowerShell/PowerShell/releases/download/v7.4.0-preview.2/PowerShell-7.4.0-preview.2-win-x64.msi"

   # Define the location to save the MSI file
   $output = "$env:TEMP\PowerShell-7-Preview.msi"

   # Download the MSI installer
   Invoke-WebRequest -Uri $url -OutFile $output

   # Install PowerShell 7 Preview
   Start-Process msiexec.exe -ArgumentList "/i $output /quiet" -Wait
   ```  

1. Run the following command to navigate to the following path:

   ```
   cd C:\Users\demouser
   ```   
   
1. Run the following command to login to Azure:

   ```
   azd auth login
   ```

   - After running the above command, a web browser tab will open and prompt you to sign into Azure. Select the Azure account you had previously logged into, or if prompted, provide your Azure username and password. Once authentication is complete, you can return to PowerShell 7.

   - Return to PowerShell 7, where you should see the message **Logged in to Azure**.

     ![](../media/Active-image104.png)

1. Once successfully logged in ,run the below command to download the project code:

   ```
   azd init -t https://github.com/CloudLabsAI-Azure/azure-search-openai-demo-nvidia
   ```
   >**Note**: The above command will initialize a git repository specific to NVIDIA LLM, eliminating the need to clone it afterwards.

1. When prompted with **Continue iniatializing an app in `C:\Users\demouser`**, type **y / yes (1)**.

   ![](../media/Active-image105.png)

1. If **What would you like to do with these files?** prompted, choose **Overwrite with versions from template**.

   ![](../media/gen3.png)

1. Enter a new environment name:  **activategenai**

   >**Note**: This will create a new folder in the `.azure` folder, and set it as the active environment for any calls to azd going forward.

   ![](../media/Active-image106.png)

1. Verify the new project initialized is successful.

   ![](../media/Active-image107.png)

1. In the PowerShell run the following commands to set the environment variables using the azd env set command.

   ``` 
   azd env set NVIDIA_NIM_ENABLED true
   azd env set NVIDIA_NIM_ENDPOINT "<your-azureml-endpoint-token>v1"  #Make sure to keep v1
   azd env set NVIDIA_NIM_API_KEY "<your-azureml-key>"
   azd env set NVIDIA_NIM_MODEL_NAME "meta/llama-3.1-8b-instruct"
   azd env set NVIDIA_NIM_DEPLOYMENT_NAME "llama3-1-8b-nim-deployment-aml-1"
   ```
   > **Note**: Replace `<your-azureml-endpoint-token>` with Azure ML endpoint and `<your-azureml-key>` with Azure ML key, also if your NIM deployment names is different then the provided one please update that too.
   
1. Run the below command to provision Azure resources and deploy the resources, including building the search index based on the files found in the `./data` folder

   ```
   azd up
   ```
   >**Note**: If prompted with the **ERROR: not logged in, run azd auth login to login** and select your **Azure Account** again.

   >**Note**: Please be aware that deploying the resources and the associated application may take up to 30 minutes.

   > **Note** : Ensure to re-run in case of any deployment failure with Storage Account.

1. Add the following details when prompted:

   - Select an Azure Subscription to use: Press **Enter** to choose the default **subscription (1)**
   - Select an Azure Location to use: **Select any location you would like to use (2)**
   - Enter a value for the 'documentIntelligenceResourceGroupLocation' infrastructure parameter: **Select any location you would like to use (3)**
   - Enter a value for the 'openAIResourceGroupLocation' infrastructure parameter: **Select any location you would like to use(4)**
     
      ![](../media/Active-image110.png)

      ![](../media/Active-image111.png)

1. After the application has been successfully deployed you will see a URL printed to the console. Copy and browse the URL to interact with the application in your browser. It will look like the following:

    ![](../media/Active-image108.png)
    ![](../media/Active-image109.png)
 
    >**Note**: It may take 30 minutes after you see 'SUCCESS' for the application to be fully deployed. If you see a "Python Developer" welcome screen or an error page, then wait a bit and refresh the page.

1. In the chat application, enter the prompt: **What does a Product Manager do?** and then press Enter. Click on the **Show thought process** icon.

   ![](../media/Active-image-new3.png)

1. Below in the **Thought Process**, you will see that the **Azure OpenAI Chat** model is utilized.

   ![](../media/Active-image-new4.png)

1. Click on **Ask a question** at the top to use he NVIDIA NIM.

   ![](../media/Active-image-new2a.png)

1. In the **Developer settings** pop-up, check the box for **Use NVIDIA NIM LLM** , then click the **Close** button.

   ![](../media/Active-image-new2b.png)

1. Enter the prompt: **What does a Product Manager do?** and then press Enter. You’ll notice that the Chat UI updates in green and is generated from NVIDIA LLM. Next, click on the **Show Thought Process** icon to get more details of the model used.

   ![](../media/Active-image-new2c.png)

1. Below in the **Thought Process**, you will see that the **llama-3.1-8b-instruct** model is utilized thats coming from AML endpoint that you have deployed in the previous challenge.

   ![](../media/Active-image-new6a.png)

## Success Criteria:

- Successful deployment of the Chat App.
- validate if the following services are successfully deployed in the RG (Resource Group).
  - App Service
  - Document Intelligence
  - Azure OpenAI
  - Shared Dashboard
  - Smart Detector Alert Rule
  - Search Service
  - Log Analytics Workspace
  - App Service Plan
  - Storage Account
- Validate if the data is populated into the storage container named `content`.
- The Chat app should be accessible using the Azure App service.

## Additional Resources:

-  Refer to the  [Azure Search OpenAI demo GitHub repository](https://github.com/cmendible/azure-search-openai-demo) for detailed information on the architecture.
-  [Azure copilot](https://learn.microsoft.com/en-us/azure/copilot/overview)

## Proceed with the next Challenge by clicking on **Next**>>.
