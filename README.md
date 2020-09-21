# 1. Preparation 

## 1.1 Preparation on Azure
1. Sign up an Azure account/ start an Azure subscription
	- could use student account to sign up and get $100 free: https://azure.microsoft.com/en-us/free/students/

2. Create a workspace using Azure portal
	- follow the instruction: https://docs.microsoft.com/en-us/azure/machine-learning/how-to-manage-workspace  
	- download the workspace's configuration file and save to the same directory as your jupyter notebook
		- open the workspace you just created by clicking on  `go to resources`
		- click on `overview` on the left sidebar
		- click on `Download config file`
		- save the file to the same directory of `StartDask.ipynb`

3. Create a "compute cluster" on Azure Machine Learning studio
	- Enter the workspace you create
	- Select `Compute` on the left side bar
	- Click on  `Compute clusters`
	- Click on `Create` or `New`
	- The suggested configuration for the new compute cluster
		- `Compute name`: dask-resource
		- `Virtual machine priority`: Dedicated
		- `Minimum number of nodes`: 0
		- `Maximum number of nodes`: 1/2
		- `Idle seconde before scale down`: 600
		- `Admin username`: daskuser
		- `admin password`: it is in your choice

4. Create an Azure Storage account
	- On the Azure portal menu, select All services. In the list of resources, type `Storage Accounts`. Select `Storage Accounts`
	- On the Storage Accounts window that appears, choose `Add`
	- Select the subscription in which to create the storage account
	- `Resource group`, select the resource group that exists
	- `Storage account name`: dask
	- `Account kind`: the default one "StorageV2 (general purpose v2)"
	- `Replication`: the default one 

5. Create a container in Azure Storage
	- Navigate to your new storage account in the Azure portal
	- In the left menu for the storage account, scroll to the Blob service section, then select `Containers`
	- Select the `+ Container` button
	- Type a name for your new container
	- Select `OK` to create the container
	
6. Upload dataset to the block blobs in that container
	- download the dataset `search_data.csv` from the repository's folder `interactive`	
	- navigate to the container you created in the previous section
	- Select the `Upload` button to open the upload blade and select the local file you want to upload 


## 1.2 Preparation in Jupyter Notebook
1. install 
	- `azureml` using `! pip install 'azureml-sdk[notebooks]'`
	- the latest `dask distributed` using `pip install --upgrade dask distributed`
	- `adlfs` using `! pip install adlfs`

# 2 Files we will used
1. There are different applications running dask on Azure cloud resources, we just use the folder `interactive` to learn how to run dask on Azure computer target
2. Within the folder `interactive`, we only run notebook `StartDask.ipynb`. After completing all the preparations above, now we need to run this notebook.

# 3 Some important concepts in Azure
- workspace: https://docs.microsoft.com/en-us/azure/machine-learning/concept-workspace
- Azure Machine Learning SDK for Python: https://docs.microsoft.com/en-us/python/api/overview/azure/ml/?view=azure-ml-py
- environment: https://docs.microsoft.com/en-us/azure/machine-learning/concept-environments
- compute target: https://docs.microsoft.com/en-us/azure/machine-learning/concept-compute-target
- data access: https://docs.microsoft.com/en-us/azure/machine-learning/concept-data
