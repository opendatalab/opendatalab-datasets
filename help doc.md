OpenDataLab supports multivariate data management. The data center provides the display, retrieval and download of public data sets, as well as the upload, management and publishing of private data sets, and supports the open sharing of user-built data sets. The data set center provides free and open source data sets for AI researchers. Through the data set center, researchers can obtain classic data sets in various fields in a unified format. Through the search function of the platform, researchers can quickly and conveniently find the data sets they need; through the unified format of the platform, researchers can easily develop tasks across data sets.


Central directory structure of data set document

Data Set Creation Process: Introduction Data Set Creation Process Upload Data Set: Upload Data Set Steps Download Data Set: Download Data Set Steps Dataset Card: Introduction Data Set Card Dataset Maintenance: Introduction to Dataset Maintenance


# Dataset creation process
## Create a dataset
Step 1: Enter the data set creation page, enter the content platform-data set center homepage, click Create to create a data set, and enter the data set creation page.

Step 2: Fill in the basic information of the data set. Fill in the basic information of the data set, including the name of the database (unique index), data set display name, cover, description, data type, task type and annotation type. Click Create Now to complete the creation of a data set.

## Upload data
Step 1: Enter the data upload page. On the data set file tab page, click Upload to enter the data upload page.

Step 2: Select the type of data to be uploaded. Select the type of data to be uploaded (file, folder, compressed package). Select to upload the compressed package to automatically decompress the compressed package.

Step 3: Start the data upload task. After selecting the file, display the read file list. Click Upload Now to start the data upload task.

Step 4: View Upload/Unzip Task Data After the upload/unzip task starts, you can view the upload/unzip task in the task list.

## Improve the introduction of data sets and submit them to the public
Step 1: Edit Data Set Introduction Click Edit Data Set Introduction in the Data Set Introduction tab to enter Data Set Meta Information Edit (metafile) and Data Set Description (README) Edit.

Step 2: Edit the metadata of the data set Edit the metadata of the data set, which supports editing the metafile. Yml through a visual form; Edit the introduction of the dataset, which improves the introduction information of the dataset by editing the README. MD file.

Step 3: Save and commit changes Save and commit changes (commit).

Step 4: Set the visibility of the data set. In the setting tab, the data set can be made public. The public data set requires license information.

<br>

# Upload the data set
This document will guide you on how to upload data in the Dataset Center.

## Uploading data through the user interface
Step 1: Go to the data upload page. On the main page of the Dataset Center, find and click the "Dataset File" tab page. On this page, you will see a button called "Upload". Click it, and you will go to the data upload page.

Step 2: Select Data Type On the Data Upload page, you need to select the data type you want to upload. There are three choices for the data type:

File Folder Compression Package

If you select "zip", the system will automatically unzip your files after uploading.

Step 3: Upload the file After selecting the data type, select the file you want to upload. You will see a list of the selected files. After confirmation, click "Upload Now" to start the data upload task.

Step 4: View the upload/unzip task Once the data upload/unzip task starts, you can view the task progress in the "Task List". This way, you can easily keep track of your upload and unzip tasks.

Data upload through CLI and Python SDK In addition to data upload through the interface, we also support data upload through CLI and Python SDK. To upload data using the CLI and Python SDK, you need to install them first. The installation codes are as follows: pip install openxlab The following are some basic examples of using the CLI and SDK. For details, please refer to the developer documentation:

Uploading files Uploading files on the CLI command line, uploading files with the upload-file parameter, uploading folders with the upload-folder parameter

```
openxlab dataset upload-file --dataset-repo <dataset-repo> --source-path <source-path> --target-path <target-path>

openxlab dataset upload-file -r <dataset-repo> -s <source-path> -t <target-path>
```


```
openxlab dataset upload-folder --dataset-repo <dataset-repo> --source-path <source-path> --target-path <target-path>

openxlab dataset upload-folder -r <dataset-repo> -s <source-path> -t <target-path>
```

Upload files in the Python SDK, upload files using the upload _ file function, and upload folders using the upload _ folder function

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

# Download the data set
This document will guide you on how to download the data in the Dataset Center.

## Downloading data through the user interface
Step 1: Enter the Dataset List Page In the main page of the Dataset Center, you will see all the datasets that you have access to.

Step 2: Select the dataset. In the dataset list, find the dataset you want to download, and click the name of the dataset to enter the dataset details page.

Step 3: Download data set On the data set details page, click the data set file tab page to view the list of all files in this data set. Click the "Download" button on the right side of each file to download a single file.

## Download data via CLI, Python SDK
In addition to downloading data through the interface, we also support downloading data through the CLI, Python SDK. To upload data using the CLI and Python SDK, you need to install them first. The installation code is as follows: pip install openxlab The following are some basic examples of using the CLI and SDK. For details, please see the developer documentation

Download DatasetUse the CLI to download the entire repository for the dataset

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

Where: | Parameter | Abbreviation | Required | Parameter Type | Parameter Description | Example |
|---|---|---|---|---|---|
|dataset-repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/repo-name|
|source-path|-s|是|String|Relative path of the file under the corresponding data set warehouse|-s /train/file|
|target-path|-t|否|String|下载仓库指定的本地路径|--target-path /path/to/local/folder|

Download Dataset Warehouse using SDK

```
from openxlab.dataset import get
get(dataset_repo='username/repo_name', target_path='/path/to/local/folder')
```

Using the SDK to Download Dataset Files

```
from openxlab.dataset import download
download(dataset_repo='username/repo_name', source_path='/train/file', target_path='/path/to/local/folder')
```

Among

|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|dataset_repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/repo-name|
|source_path|-s|是|String|对应数据集仓库下文件的相对路径|-s /path/to/local/folder|
|target_path|-t|否|String|下载仓库指定的本地路径|--target-path /path/to/local/folder|



# Data set card
On the main page of the data set center, find and click the tab page of "Data Set Introduction", and click "Edit Data Set Introduction" to edit the introduction information and meta information of the data set:

Edit the data set introduction page by editing the README file. Edit the metadata of the data set by editing metafile. The metadata includes data type, task type, annotation type, license, etc., and is edited in a visual form. The upper part of the data set introduction (README) is the README editing area, which supports both editing and preview views. README can also be uploaded by the user. The entry is the file upload of "data set file".

README example

```
# 数据集名称

## 简介

- **数据来源：** 这部分简单描述数据的来源，例如是公开数据集、公司内部数据集、爬虫数据等。

- **数据量和格式：** 这部分描述数据集的大小，包括数据量（例如多少行、多少个实例）、特征数量等，并简要描述数据的格式，例如csv文件，每行一个json等。

- **特征描述：** 这部分详细描述每个特征的含义，类型，以及如果有的话，特征的可能取值范围。

## 数据集任务

描述数据集主要用于什么任务，例如文本分类、目标检测、语音识别等。

## 数据预处理

如果有的话，描述数据预处理的过程，例如缺失值处理、特征选择、特征提取、数据清洗等。

## 引文
```

# Dataset meta information (metafile)
The lower part is the metafile editing area, which is edited through the visual form. The metafile is automatically generated when the data set is created. If the data type, task type, annotation type, name and other information are filled in during creation, the corresponding field of the metafile will be automatically filled. Select the Chinese and English labels in the visual configuration, and automatically fill in the English labels in yaml.

## Description of the metafile field
|English name|中文名称|填写方式|说明|
|---|---|---|---|
|displayName|名称|输入|Only Chinese and English, numbers,-, and _ are supported|
|license|开源协议|下拉|公开数据集必填|
|taskTypes|任务类型|下拉|-|
|mediaTypes|数据类型|下拉|-|
|labelTypes|标注类型|下拉|-|
|tags|标签|输入|Custom labels|
|publisher|发布机构|下拉|-|
|publishDate|发布时间|输入|Input in standard format, example: 2023-06-15|
|publishUrl|发布首页|输入|-|
|paperUrl|发布论文|输入|-|

# Dataset maintenance
In the "Settings" tab, you can maintain the basic information of the dataset, including changing the cover, changing the description of the dataset, changing the status of the dataset and deleting the dataset warehouse.

## Dataset basic information
Editable dataset information includes:

Dataset cover, support clicking to upload the cover again. Data set description, which supports the modification of data set description.

## Dataset visibility
Support data set public/private state switching.

## Delete Dataset Warehouse
It is a high-risk operation and requires careful operation.


# Dataset CLI (Command Line Utility)
## Overview
Puyuan Content Platform Command Line Tools (openxlab Command Line Interface) provides command line tools for publishers in the data set center. This tool enables you to manage Dataset Center, and the content resources contributed by Dataset Center.

The command line structure specification of Puyuan Content Platform CLI tool is as follows:

```
openxlab  <command > <subcommand >  [options and parameters]
```
Openxlab: The name of the CLI tool of the openxlab Puyuan Content Platform command: Specifies a top-level command (case-insensitive, default lowercase) that typically indicates the name of a submodule or product supported in the command-line tool, such as dataset, data, app, etc. Or functional commands that represent the command-line tool itself, such as help, config, and so on. Subcommand: Specifies an additional subcommand to perform an action, that is, a specific action. Options and parameters: Specifies options or API parameter options that control CLI behavior. The option values can be numbers, strings, JSON structure strings, and so on.

## Installation guide
**Install using pip**

```
pip install openxlab
```
Release address: https://pypi.org/project/openxlab/ (opens new window)

**Unload**

```
pip uninstall openxlab
```

## Configuration guide
Before formally using **Setting of AK and SK** the SDK/CLI, it is necessary to complete the local configuration of AK/SK of the Puyuan content platform account, otherwise the identity verification cannot be passed when using the SDK/CL to access the Puyuan content platform. Please refer to the configuration method: [鉴权管理](https://openxlab.org.cn/docs/developers/%E9%89%B4%E6%9D%83%E7%AE%A1%E7%90%86.html)

Dataset Center CLI Features Features Overview Dataset Info View dataset info Dataset File List View dataset ls dataset Create dataset Create dataset Upload file dataset Upload-file dataset Upload folder dataset Upload-folder dataset download dataset get dataset file download dataset download dataset commit modify dataset commit dataset repository delete dataset remove

## Dataset information viewing dataset info

```
openxlab dataset info --dataset-repo <dataset-repo>
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|--dataset-repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/repo-name|

Example:

```
openxlab dataset info --dataset-repo my_dataset_name
openxlab dataset info -r my_dataset_name
```

## Dataset file list viewing dataset ls

```
openxlab dataset ls --dataset-repo <dataset-repo>
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|--dataset-repo	-r|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/repo-name|

Example:

```
openxlab dataset ls --dataset-repo my_dataset_name
openxlab dataset ls -r my_dataset_name
```

## Dataset createdataset create

```
openxlab dataset create --repo-name <repo-name>
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|--repo-name|无|是|String|The name of the data set warehouse, which, together with the user name, forms the data set warehouse address|dataset_name|

For example, when creating a warehouse, you need to fill in the name of the dataset warehouse, and the visibility of the dataset is private by default

```
openxlab dataset create --repo-name dataset_name
```

## Dataset upload file dataset upload-file

```
openxlab dataset upload-file --dataset-repo <dataset-repo> 
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|--dataset-repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/repo-name|
|--source-path|-s|是|String|上传本地文件的所在的路径|-s /path/to/local/folder/1.jpg|
|--target-path|-t|否|String|Corresponding to the relative path under the data set warehouse. If not added, it will be uploaded to the root directory of the warehouse.|-t /raw/train|

Example:

```
openxlab dataset upload-file --dataset-repo username/repo-name 
            --source-path /path/to/local/folder/1.jpg
            --target-path /raw/train

openxlab dataset upload-file -r username/repo-name
            -s /path/to/local/folder/1.jpg
            -t /raw/train
```

## Dataset upload folder dataset upload-folder

```
openxlab dataset upload-folder --dataset-repo <dataset-repo> 
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|--dataset-repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/repo-name|
|--source-path|-s|是|String|上传本地文件夹的所在的路径|-s /path/to/local/folder|
|--target-path|-t|否|String|Corresponding to the relative path under the data set warehouse. If not added, it will be uploaded to the root directory of the warehouse.|-t /raw/train|

Example:

```
openxlab dataset upload-folder --dataset-repo username/repo-name
            --source-path /path/to/local/folder
            --target-path /raw/train

openxlab dataset upload-folder -r username/repo-name
            -s /path/to/local/folder
            -t /raw/train
```

## Data set download dataset get

```
openxlab dataset get --dataset-repo <dataset-repo> 
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|--dataset-repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|	zhangsan/dataset-repo-name|
|--target-path|-t|否|String|下载仓库指定的本地路径|--target-path /path/to/local/folder|

Example:

```
openxlab dataset get --dataset-repo username/repo-name
                  --target-path /path/to/local/folder

openxlab dataset get -r username/repo-name 
                  -t /path/to/local/folder
```

## Dataset file download dataset download

```
openxlab dataset download --dataset-repo <dataset-repo> 
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|--dataset-repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/repo-name|
|--source-path|-s|是|String|Relative path of the file under the corresponding data set warehouse|-s /train/file|
|--target-path|-t|否|String|下载仓库指定的本地路径|--target-path /path/to/local/folder|

Example:

```
openxlab dataset download --dataset-repo username/repo-name
            --source-path /train/file
            --target-path /path/to/local/folder

openxlab dataset download -r username/repo-name
            -s /train/file
            -t /path/to/local/folder
```
## Dataset commit modify dataset commit

```
openxlab dataset commit --dataset-repo <dataset-repo> 
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|--dataset-repo|-r|是|String|数据集仓库的地址，由 username/repo-name 组成|--dataset-repo='/zhangsan/repo-name'|
|--commit-message|-m|是|String|提交信息|--commit-message 'uploading'|

Example:

```
openxlab dataset commit --dataset-repo username/repo-name --commit-message 'my first commit'

openxlab dataset commit -r username/repo-name -m 'my first commit'
```

## Dataset warehouse removing dataset remove

```
openxlab dataset remove --dataset-repo <dataset-repo>
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|--dataset-repo|-r|是|String|Address of the data set repository, consisting of username/repo-name|zhangsan/repo-name|

For example, if you want to delete a warehouse, you need to fill in the name of the data set warehouse, and the deletion operation is irreversible

```
openxlab dataset remove --dataset-repo my_dataset_name
openxlab dataset remove -r my_dataset_name
```


# Dataset Python SDK

## Overview
The Python SDK for Puyuan Content Platform-Dataset Center is designed to provide developers with a programmatic way to manage and operate the functions of the Dataset Center Platform so that they can easily interact with the Datasets Center and manage datasets. Developers can programmatically perform the following tasks:

View dataset meta information and file list Create and modify datasets: Create datasets, upload files, upload folders Download datasets: Download the entire dataset repository, dataset files The Python SDK of Puyuan Content Platform-Model Center is designed to provide developers with programmatic ways to manage and operate the functions of the Model Center Platform. So that they can easily interact with the Model Center and model management. Through the inference interface provided by Python SDK, developers can call different models efficiently and realize the development of model applications. The Python SDK enables developers to programmatically perform the following tasks:

View the dataset: View the metadata and file list of the dataset Create and modify the dataset: Create the dataset, upload the file, and upload the folder Download the dataset: Download the entire dataset warehouse and dataset files Using the Python SDK of the dataset platform, developers can manage and use datasets more easily and improve their work efficiency.

## Installation guide
Install the SDK using pip

```
pip install openxlab
```
Release address: https://pypi.org/project/openxlab/.

Uninstall the SDK

```
pip uninstall openxlab
```

## Authentication of SDK
Configuration method 1: configure AK/SK for authentication through the openxlab. Login () function

Implement authentication through the provided login () function, and fill in the corresponding Access key and Secret key in the function. The usage method is as follows:

```
import openxlab
openxlab.login(ak=<Access Key>, sk=<Secrete Key>)
```

Configuration mode 2: Configure environment variables in application settings, and configure AK/SK for authentication

You can find [Application Configuration] to set environment variables on the settings page of the application created by individuals. You can set the Access key to an environment variable named OPENXLAB _ AK and the Secret key to an environment variable named OPENXLAB _ SK.


Function overview Data set meta information View info Data set file list View query Data set Create create _ repo Data set Upload file upload _ file Data set Upload folder upload _ folder Data set Repository Download get Data set File Download The download data set commits the modification commit data set warehouse to delete the remove _ repo.

Dataset Meta Info View info

```
from openxlab.dataset import info
info(dataset_repo='username/repo_name')
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
| | dataset _ repo | -r | is | String | the address of the data set repository, consisting of username/repo _ name | zhangsan/ceshi |

## Dataset file list viewing query

```
from openxlab.dataset import query
query(dataset_repo='username/repo_name')
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|dataset_repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/ceshi|

## Dataset creation create _ repo.

```
from openxlab.dataset import create_repo
create_repo(repo_name='repo_name')
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|repo_name|无|是|String|The name of the data set warehouse, which, together with the user name, forms the data set warehouse address|ceshi|

## Dataset upload file upload _ file

```
from openxlab.dataset import upload_file
upload_file(dataset_repo='username/repo_name')
              source_path='/path/to/local/file', target_path='/train')
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|dataset_repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/repo-name|
|source_path|-s|是|String|上传本地文件的所在的路径|source_path='/path/to/local/folder/1.jpg'|
|target_path|-t|否|String|Corresponding to the relative path under the data set warehouse. If not added, it will be uploaded to the root directory of the warehouse.|target_path='/train'|

## Dataset upload folder upload _ folder

```
from openxlab.dataset import upload_folder
upload_folder(dataset_repo='username/repo_name')
              source_path='/path/to/local/folder', target_path='/train')
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|dataset_repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/repo-name|
|source_path|-s|是|String|上传本地文件的所在的路径|source_path='/path/to/local/folder'|
|target_path|-t|否|String|Corresponding to the relative path under the data set warehouse. If not added, it will be uploaded to the root directory of the warehouse.|target_path='/train'|

## Dataset warehouse download get

```
from openxlab.dataset import get
get(dataset_repo='username/repo_name', target_path='/path/to/local/folder')
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|dataset_repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/repo_name|
|target_path|-t|否|String|下载仓库指定的本地路径|target_path='/path/to/local/folder'|

## Data set file download

```
from openxlab.dataset import download
download(dataset_repo='username/repo_name')
              source_path='/train/file', target_path='/path/to/local/folder')
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|dataset_repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/repo-name|
|source_path|-s|是|String|对应数据集仓库下文件的相对路径|source_path='/train/file'|
|target_path|-t|否|String|下载仓库指定的本地路径|target_path='/path/to/local/folder'|

## Dataset commit modify commit

```
from openxlab.dataset import commit
commit(dataset_repo='username/repo_name', commit_message='my first commit.')
```

```
from openxlab.dataset import commit
commit(dataset_repo='username/repo_name'，commit_message='my first commit.')
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|dataset_repo|-r|是|String|Address of the data set repository, consisting of username/repo _ name.|dataset_repo='/zhangsan/ceshi'|
|commit_message|-m|是|String|提交信息|commit_message='my first commit.'|

## Dataset Warehouse Delete remove _ repo.

```
from openxlab.dataset import remove_repo
remove_repo(dataset_repo='username/repo_name')
```
|参数|缩写|Required or not|参数类型|参数说明|示例|
|---|---|---|---|---|---|
|dataset_repo|无|是|String|Address of the data set repository, consisting of username/repo _ name.|zhangsan/ceshi|