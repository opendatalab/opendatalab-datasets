OpenDataLab supports multivariate data management. The data center provides the display, retrieval and download of public data sets, as well as the upload, management and publishing of private data sets, and supports the open sharing of user-built data sets. The data set center provides free and open source data sets for AI researchers. Through the data set center, researchers can obtain classic data sets in various fields in a unified format. Through the search function of the platform, researchers can quickly and conveniently find the data sets they need; through the unified format of the platform, researchers can easily develop tasks across data sets.


# Dataset creation process
## Overview
### Create a dataset
**Step 1: Enter the dataset creation page,**  
enter the content platform-data set center homepage, click Create to create a data set, and enter the data set creation page.

**Step 2: Fill in the basic information of the dataset.**  
Fill in the basic information of the data set, including the name of the database (unique index), data set display name, cover, description, data type, task type and annotation type. Click Create Now to complete the creation of a data set.

### Upload data
**Step 1: Enter the data upload page.**  
On the data set file tab page, click Upload to enter the data upload page.

**Step 2: Select the type of data to be uploaded.**   
Select the type of data to be uploaded (file, folder, compressed package). Select to upload the compressed package to automatically decompress the compressed package.

**Step 3: Start the data upload task.**   
After selecting the file, display the read file list. Click Upload Now to start the data upload task.

**Step 4: View Upload/Unzip Task Data**  
After the upload/unzip task starts, you can view the upload/unzip task in the task list.

### Improve the introduction of data sets and submit them to the public
**Step 1: Edit Data Set Introduction**  
Click Edit Data Set Introduction in the Data Set Introduction tab to enter Data Set Meta Information Edit (metafile) and Data Set Description (README) Edit.

**Step 2: Edit the metadata of the dataset**   
Edit the metadata of the data set, which supports editing the metafile. Yml through a visual form; Edit the introduction of the dataset, which improves the introduction information of the dataset by editing the README. MD file.

**Step 3: Save and commit changes**  
Save and commit changes (commit).

**Step 4: Set the visibility of the dataset.**   
In the setting tab, the data set can be made public. The public data set requires license information.

---

## Upload the dataset
This document will guide you on how to upload data in the Dataset Center. There are 2 ways:

### 1. Uploading data through the user interface  
**Step 1: Go to the data upload page.**   
On the main page of the Dataset Center, find and click the "Dataset File" tab page. On this page, you will see a button called "Upload". Click it, and you will go to the data upload page.

**Step 2: Select Data Type**  
On the Data Upload page, you need to select the data type you want to upload. There are three choices for the data type:

- File
- Folder
- Compression Package

If you select "zip", the system will automatically unzip your files after uploading.

**Step 3: Upload the file**  
After selecting the data type, select the file you want to upload. You will see a list of the selected files. After confirmation, click "Upload Now" to start the data upload task.

**Step 4: View the upload/unzip task**  
Once the data upload/unzip task starts, you can view the task progress in the "Task List". This way, you can easily keep track of your upload and unzip tasks.

### 2. Data upload through CLI and Python SDK

In addition to data upload through the interface, we also support data upload through CLI and Python SDK. To upload data using the CLI and Python SDK, you need to install them first. The installation codes are as follows: `pip install openxlab` The following are some basic examples of using the CLI and SDK. For details, please refer to the developer documentation:

**Uploading files**  

on the CLI command line, uploading files with the `upload-file` parameter, uploading folders with the `upload-folder` parameter

```
openxlab dataset upload-file --dataset-repo <dataset-repo> --source-path <source-path> --target-path <target-path>

openxlab dataset upload-file -r <dataset-repo> -s <source-path> -t <target-path>
```


```
openxlab dataset upload-folder --dataset-repo <dataset-repo> --source-path <source-path> --target-path <target-path>

openxlab dataset upload-folder -r <dataset-repo> -s <source-path> -t <target-path>
```

Upload files in the Python SDK, upload files using the `upload _ file` function, and upload folders using the `upload _ folder` function

```
from openxlab.dataset import upload_file
upload_file(dataset_repo='username/repo_name', 
             source_path='/path/to/local/file', target_path='/train')
```

```
from openxlab.dataset import upload_folder
upload_folder(dataset_repo='username/repo_name', 
               source_path='/path/to/local/folder', target_path='/train')
```

---

## Download the dataset
This document will guide you on how to download the data in the Dataset Center. There are 2 ways:

### 1. Downloading data through the user interface
**Step 1: Enter the Dataset List Page**  
In the main page of the Dataset Center, you will see all the datasets that you have access to.

**Step 2: Select the dataset**   
In the dataset list, find the dataset you want to download, and click the name of the dataset to enter the dataset details page.

**Step 3: Download dataset**   
On the dataset details page, click the data set file tab page to view the list of all files in this data set. Click the "Download" button on the right side of each file to download a single file.

### 2. Download data via CLI, Python SDK
In addition to downloading data through the interface, we also support downloading data through the CLI, Python SDK. To upload data using the CLI and Python SDK, you need to install them first. The installation code is as follows: `pip install openxlab` The following are some basic examples of using the CLI and SDK. For details, please see the developer documentation

**Download Dataset**  
Use the CLI to download the entire repository for the dataset

```
openxlab dataset get --dataset-repo username/repo-name
                     --target-path /path/to/local/folder

openxlab dataset get -r username/repo-name 
                     -t /path/to/local/folder
```

Using the CLI to Download a Dataset File

```
openxlab dataset download --dataset-repo username/repo-name
                          --source-path /train/file
                          --target-path /path/to/local/folder

openxlab dataset download -r username/repo-name
                          -s /train/file
                          -t /path/to/local/folder
```

Among：
| Parameter | Abbreviation | Required | Parameter Type | Parameter Description | Example |
|---|---|---|---|---|---|
|dataset_repo|-r|yes|String|Address of the dataset repository, consisting of `username/repo_name`|zhangsan/repo-name|
|source_path|-s|yes|String|Relative path of the file under the corresponding data set warehouse|-s /train/file|
|target_path|-t|no|String|Download the local path specified by the warehouse|--target-path /path/to/local/folder|

Download Dataset repository using SDK

```
from openxlab.dataset import get
get(dataset_repo='username/repo_name', target_path='/path/to/local/folder')
```

Using the SDK to Download Dataset Files

```
from openxlab.dataset import download
download(dataset_repo='username/repo_name', source_path='/train/file', target_path='/path/to/local/folder')
```

Among：

| Parameter | Abbreviation | Required | Parameter Type | Parameter Description | Example |
|---|---|---|---|---|---|
|dataset_repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/repo-name|
|source_path|-s|yes|String|Relative path to the file in the corresponding data set warehouse|-s /path/to/local/folder|
|target_path|-t|no|String|Download the local path specified by the warehouse|--target-path /path/to/local/folder|

---

## Dataset card
On the main page of the data set center, find and click the tab page of "Data Set Introduction", and click "Edit Data Set Introduction" to edit the introduction information and meta information of the dataset:

- Edit the dataset introduction page by editing the README file.
- Edit the metadata of the data set by editing metafile. The metadata includes data type, task type, annotation type, license, etc., and is edited in a visual form.

### Dataset introduction (README)
The upper part of the dataset introduction (README) is the README editing area, which supports both editing and preview views. README can also be uploaded by the user. The entry is the file upload of "data set file".

**Example**

```
# Dataset name

## Introdution

- **Data source:** This section briefly describes the source of the data, such as public data sets, company internal data sets, crawler data, etc.

- **Data volume and format:** This part describes the size of the data set, including data volume (such as how many rows, how many instances), number of features, etc., and briefly describes the format of the data, such as a csv file, one json per line wait.

- **Feature Description:** This section describes in detail the meaning, type, and, if any, possible value range of the feature for each feature.

## Dataset tasks

Describe what tasks the data set is mainly used for, such as text classification, object detection, speech recognition, etc.

## Data preprocessing

If any, describe the data preprocessing process, such as missing value processing, feature selection, feature extraction, data cleaning, etc.

## Citation
```

### Dataset meta information (metafile)
The lower part is the metafile editing area, which is edited through the visual form. The metafile is automatically generated when the data set is created. If the data type, task type, annotation type, name and other information are filled in during creation, the corresponding field of the metafile will be automatically filled. Select the Chinese and English labels in the visual configuration, and automatically fill in the English labels in yaml.

### Description of the metafile field
|English name|Chinese name|Filling method|Instructions|
|---|---|---|---|
|displayName|Name|Input|Only Chinese and English, numbers,-, and _ are supported|
|license|Open Source Agreement|Drop-down|Required for public datasets|
|taskTypes|Task type|Drop-down|-|
|mediaTypes|Data types|Drop-down|-|
|labelTypes|Label type|Drop-down|-|
|tags|Tags|Input|Custom labels|
|publisher|Publishing agency|Drop-down|-|
|publishDate|Publish time|Input|Input in standard format, example: 2023-06-15|
|publishUrl|Publish homepage|Input|-|
|paperUrl|Publish paper|Input|-|

---

## Dataset maintenance
In the "Settings" tab, you can maintain the basic information of the dataset, including changing the cover, changing the description of the dataset, changing the status of the dataset and deleting the dataset warehouse.

### Dataset basic information
Editable dataset information includes:

● Dataset cover, support clicking to upload the cover again.   
● Dataset description, which supports the modification of data set description.

### Dataset visibility
Support data set public/private state switching.

### Delete Dataset Warehouse
It is a high-risk operation and requires careful operation.

---

# Authentication management

OpenXLab's OpenAPI uses Access Key & Secret Key for authentication. All registered accounts will be assigned a pair of AK and SK by default, which you can manage by entering the [personal center](https://sso.openxlab.org.cn/login). Login to OpenXLab Content Platform-Personal-Account and Security [Key Management] to view the AK/SK of the current account. If it is empty, click Add Key to add a pair of keys.

Please note that your AK and SK are private. Please do not share it with others or save it on any client/APP, nor use any version management tools to push it to the public network. For production scenarios, all OpenAPI calls need to be routed through the backend service, and the API Key can be read through environment variables or other key management services.

If AK and SK are leaked, you can enter the [personal center](https://sso.openxlab.org.cn/login) to delete this certificate and regenerate it. Note that this operation will invalidate all API_KEY generated using the AK and SK.

## AK and SK settings
Before officially using the SDK/CLI, you need to complete the local configuration of the AK/SK of the Puyuan Content Platform account, otherwise the identity verification cannot be passed when using the SDK/CL to access the Puyuan Content Platform.

**Configuration method 1:**  
Configure through CLI commands

1. It is recommended to use Puyuan openxlab command line tool to configure AK/SK. The command line tool can be installed through `pip install openxlab`. After completing the installation of the command line tool, configure it through the login command.
```
openxlab login

OpenXLab Access Key ID: xxxxxxxxxxxxxxxxxxxx
OpenXLab Secret Access Key: xxxxxxxxxxxxxxxxxxx
```

2. Use the openxlab login command to enter the corresponding `Access key`and `Secret key` as prompted. After completion, the `config.json` file will be generated in the `~/.openxlab` directory with the following format:
```
{
    "ak": "vmb1akg9w1xwdrxnyxlr",
    "sk": "9gvpqrel6jez23ywerzvbz2dbpq4y8b1aow5nngx"
}
```

**Configuration method 2:**  
Configure by creating a `config.json` file

Create the corresponding `config.json file` directly in the `~/.openxlab` directory, fill in the corresponding `Access key` and `Secret key`, the format is as follows:
```
{
    "ak": "vmb1akg9w1xwdrxnyxlr",
    "sk": "9gvpqrel6jez23ywerzvbz2dbpq4y8b1aow5nngx"
}
```

### SDK authentication
**Configuration method 1:**  
Configure through the `openxlab.login()` function AK / SK for authentication

Authentication is implemented through the provided `login() `function, and the corresponding `Access key` and `Secret key` are filled in the function. The usage method is as follows:
```
import openxlab
openxlab.login(ak=<Access Key>, sk=<Secret Key>)
```

**Configuration method 2:**   
Configure environment variables in application settings and configure AK / SK for authentication

You can find [Application Configuration] on the settings page of a personally created application to set environment variables. You can set the `Access key` to the environment variable named `OPENXLAB_AK` and the `Secret key` to the environment variable named `OPENXLAB_SK`.

---

# Dataset CLI (Command Line Utility)
## Overview
OpenXLab Command Line Interface provides command line tools for publishers in the data set center. This tool enables you to manage Dataset Center, and the content resources contributed by Dataset Center.

**The command line structure specification of Puyuan Content Platform CLI tool is as follows:**

```
openxlab  <command > <subcommand >  [options and parameters]
```
● `Openxlab`: The name of the CLI tool of the openxlab Puyuan Content Platform   
● `command`: Specifies a top-level command (case-insensitive, default lowercase)
  - that typically indicates the name of a submodule or product supported in the command-line tool, such as dataset, data, app, etc.
  - Or functional commands that represent the command-line tool itself, such as help, config, and so on.
● `Subcommand`: Specifies an additional subcommand to perform an action, that is, a specific action.  
● `Options and parameters`: Specifies options or API parameter options that control CLI behavior. The option values can be numbers, strings, JSON structure strings, and so on.

## Installation guide
**Install using pip**

```
pip install openxlab
```
Release address: https://pypi.org/project/openxlab

**Unload**

```
pip uninstall openxlab
```

## Configuration guide  

**AK and SK settings**
Before formally using **Setting of AK and SK** the SDK/CLI, it is necessary to complete the local configuration of AK/SK of the Puyuan content platform account, otherwise the identity verification cannot be passed when using the SDK/CL to access the Puyuan content platform. Please refer to the configuration method: [Authentication management](#Authentication-management)

## Dataset Center CLI Features

### Dataset information viewing (dataset info)

```
openxlab dataset info --dataset-repo <dataset-repo>
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|--dataset-repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/repo-name|

Example:

```
openxlab dataset info --dataset-repo my_dataset_name
openxlab dataset info -r my_dataset_name
```

### Dataset file list viewing (dataset ls)

```
openxlab dataset ls --dataset-repo <dataset-repo>
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|--dataset-repo	-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/repo-name|

Example:

```
openxlab dataset ls --dataset-repo my_dataset_name
openxlab dataset ls -r my_dataset_name
```

### Dataset create (dataset create)

```
openxlab dataset create --repo-name <repo-name>
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|--repo-name|-|yes|String|The name of the data set warehouse, which, together with the user name, forms the data set warehouse address|dataset_name|

For example, when creating a warehouse, you need to fill in the name of the dataset warehouse, and the visibility of the dataset is private by default

```
openxlab dataset create --repo-name dataset_name
```

### Dataset upload file (dataset upload-file)

```
openxlab dataset upload-file --dataset-repo <dataset-repo> 
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|--dataset-repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/repo-name|
|--source-path|-s|yes|String|The path where the local file is uploaded|-s /path/to/local/folder/1.jpg|
|--target-path|-t|no|String|Corresponding to the relative path under the data set warehouse. If not added, it will be uploaded to the root directory of the warehouse.|-t /raw/train|

Example:

```
openxlab dataset upload-file --dataset-repo username/repo-name 
            --source-path /path/to/local/folder/1.jpg
            --target-path /raw/train

openxlab dataset upload-file -r username/repo-name
            -s /path/to/local/folder/1.jpg
            -t /raw/train
```

### Dataset upload folder (dataset upload-folder)

```
openxlab dataset upload-folder --dataset-repo <dataset-repo> 
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|--dataset-repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/repo-name|
|--source-path|-s|yes|String|The path to upload the local folder|-s /path/to/local/folder|
|--target-path|-t|no|String|Corresponding to the relative path under the data set warehouse. If not added, it will be uploaded to the root directory of the warehouse.|-t /raw/train|

Example:

```
openxlab dataset upload-folder --dataset-repo username/repo-name
            --source-path /path/to/local/folder
            --target-path /raw/train

openxlab dataset upload-folder -r username/repo-name
            -s /path/to/local/folder
            -t /raw/train
```

### Dataset download `dataset get`

```
openxlab dataset get --dataset-repo <dataset-repo> 
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|--dataset-repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|	zhangsan/dataset-repo-name|
|--target-path|-t|no|String|Download the local path specified by the warehouse|--target-path /path/to/local/folder|

Example:

```
openxlab dataset get --dataset-repo username/repo-name
                  --target-path /path/to/local/folder

openxlab dataset get -r username/repo-name 
                  -t /path/to/local/folder
```

### Dataset file download (dataset download)

```
openxlab dataset download --dataset-repo <dataset-repo> 
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|--dataset-repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/repo-name|
|--source-path|-s|yes|String|Relative path of the file under the corresponding data set warehouse|-s /train/file|
|--target-path|-t|no|String|Download the local path specified by the warehouse|--target-path /path/to/local/folder|

Example:

```
openxlab dataset download --dataset-repo username/repo-name
            --source-path /train/file
            --target-path /path/to/local/folder

openxlab dataset download -r username/repo-name
            -s /train/file
            -t /path/to/local/folder
```
### Dataset commit modify (dataset commit)

```
openxlab dataset commit --dataset-repo <dataset-repo> 
```

|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|--dataset-repo|-r|yes|String|The address of the data set warehouse, consisting of `username/repo_name`|--dataset-repo='/zhangsan/repo-name'|
|--commit-message|-m|yes|String|Submit Information|--commit-message 'uploading'|

Example:

```
openxlab dataset commit --dataset-repo username/repo-name --commit-message 'my first commit'

openxlab dataset commit -r username/repo-name -m 'my first commit'
```

### Dataset warehouse removing (dataset remove)

```
openxlab dataset remove --dataset-repo <dataset-repo>
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|--dataset-repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/repo-name|

For example, if you want to delete a warehouse, you need to fill in the name of the data set warehouse, and the deletion operation is irreversible

```
openxlab dataset remove --dataset-repo my_dataset_name
openxlab dataset remove -r my_dataset_name
```

---

# Dataset Python SDK

## Overview
The Python SDK for Puyuan Content Platform-Dataset Center is designed to provide developers with a programmatic way to manage and operate the functions of the Dataset Center Platform so that they can easily interact with the Datasets Center and manage datasets. Developers can programmatically perform the following tasks:

● View dataset meta information and file list  
● Create and modify datasets: Create datasets, upload files, upload folders  
● Download datasets: Download the entire dataset repository, dataset files  

The Python SDK of OpenXLab Content Platform-Model Center is designed to provide developers with programmatic ways to manage and operate the functions of the Model Center Platform. So that they can easily interact with the Model Center and model management. Through the inference interface provided by Python SDK, developers can call different models efficiently and realize the development of model applications. The Python SDK enables developers to programmatically perform the following tasks:

● **View the dataset:** View the metadata and file list of the dataset  
● **Create and modify the dataset:** Create the dataset, upload the file, and upload the folder  
● **Download the dataset:** Download the entire dataset warehouse and dataset files Using the Python SDK of the dataset platform, developers can manage and use datasets more easily and improve their work efficiency.

## Installation guide
**Install the SDK using pip**

```
pip install openxlab
```
Release address: https://pypi.org/project/openxlab/.

**Uninstall the SDK**

```
pip uninstall openxlab
```

## Authentication of SDK
**Configuration method 1:**   
configure AK/SK for authentication through the `openxlab. Login ()` function

Implement authentication through the provided `login ()` function, and fill in the corresponding `Access key` and `Secret key` in the function. The usage method is as follows:

```
import openxlab
openxlab.login(ak=<Access Key>, sk=<Secrete Key>)
```

**Configuration mode 2:**   
Configure environment variables in application settings, and configure AK/SK for authentication

You can find [Application Configuration] to set environment variables on the settings page of the application created by individuals. You can set the `Access key` to an environment variable named `OPENXLAB_AK` and the `Secret key` to an environment variable named `OPENXLAB_SK`.

## Function overview

### Dataset Meta Info View (info)

```
from openxlab.dataset import info
info(dataset_repo='username/repo_name')
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
| | dataset _ repo | -r | yes | String | the address of the data set repository, consisting of `username/repo_name`| zhangsan/ceshi |

### Dataset file list viewing (query)

```
from openxlab.dataset import query
query(dataset_repo='username/repo_name')
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|dataset_repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/ceshi|

### Dataset creation (create_repo)

```
from openxlab.dataset import create_repo
create_repo(repo_name='repo_name')
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|repo_name|-|yes|String|The name of the data set warehouse, which, together with the user name, forms the data set warehouse address|ceshi|

### Dataset upload file (upload_file)

```
from openxlab.dataset import upload_file
upload_file(dataset_repo='username/repo_name')
              source_path='/path/to/local/file', target_path='/train')
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|dataset_repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/repo-name|
|source_path|-s|yes|String|The path where the local file is uploaded|source_path='/path/to/local/folder/1.jpg'|
|target_path|-t|no|String|Corresponding to the relative path under the data set warehouse. If not added, it will be uploaded to the root directory of the warehouse.|target_path='/train'|

### Dataset upload folder (upload_folder)

```
from openxlab.dataset import upload_folder
upload_folder(dataset_repo='username/repo_name')
              source_path='/path/to/local/folder', target_path='/train')
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|dataset_repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/repo-name|
|source_path|-s|yes|String|The path where the local file is uploaded|source_path='/path/to/local/folder'|
|target_path|-t|no|String|Corresponding to the relative path under the data set warehouse. If not added, it will be uploaded to the root directory of the warehouse.|target_path='/train'|

### Dataset warehouse download (get)

```
from openxlab.dataset import get
get(dataset_repo='username/repo_name', target_path='/path/to/local/folder')
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|dataset_repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/repo_name|
|target_path|-t|no|String|Download the local path specified by the warehouse|target_path='/path/to/local/folder'|

### Data set file (download)

```
from openxlab.dataset import download
download(dataset_repo='username/repo_name')
              source_path='/train/file', target_path='/path/to/local/folder')
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|dataset_repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/repo-name|
|source_path|-s|yes|String|Relative path to the file in the corresponding data set warehouse|source_path='/train/file'|
|target_path|-t|no|String|Download the local path specified by the warehouse|target_path='/path/to/local/folder'|

### Dataset commit modify (commit)

```
from openxlab.dataset import commit
commit(dataset_repo='username/repo_name', commit_message='my first commit.')
```

```
from openxlab.dataset import commit
commit(dataset_repo='username/repo_name'，commit_message='my first commit.')
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|dataset_repo|-r|yes|String|Address of the data set repository, consisting of `username/repo_name`|dataset_repo='/zhangsan/ceshi'|
|commit_message|-m|yes|String|Submit Information|commit_message='my first commit.'|

### Dataset Warehouse Delete (remove_repo)

```
from openxlab.dataset import remove_repo
remove_repo(dataset_repo='username/repo_name')
```
|Parameter|Abbreviation|Required or not|Parameter type|Parameter description|Example|
|---|---|---|---|---|---|
|dataset_repo|-|yes|String|Address of the data set repository, consisting of `username/repo_name`|zhangsan/ceshi|
