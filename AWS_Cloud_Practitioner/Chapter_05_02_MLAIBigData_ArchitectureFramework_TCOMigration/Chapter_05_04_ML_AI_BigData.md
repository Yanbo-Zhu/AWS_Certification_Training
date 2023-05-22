# 1 Introduction to ML and AI
10:32:36 Introduction to ML and AI

**What is Artificial Intelligence (AI)?**
Machines that perform jobs that mimic human behavior

**What is Machine Learning (ML)?**
Machines that get better at a task without explicit programming

**What is Deep Learning (DL)?**
Machines that have an artificial neural network inspired by the human brain to solve complex problems.


相关的 AWS Services 
- **Amazon SageMaker** is a fully managed service to **build, train, and deploy machine learning models** at scale
    -   **Apache MXNet on AWS**, open-source deep learning framework
    -   **TensorFlow on AWS** open-source machine intelligence library
    -   **PyTorch on AWS** open-source machine learning framework
- **Amazon SageMaker Ground Truth** 
    - is **data-labeling service**. 
    - Have humans label a dataset that will be used to train machine learning models
- **Amazon Augmented AI** human-intervention review service. 
    - When SageMaker’s uses machine Learning to make a prediction is not confident it has the right answer queue up the predication for human review.

# 2 AI and ML Services
10:34:28 AI and ML Services

- **Amazon CodeGuru** 
    - is **machine-learning code analysis service**. 
    - CodeGuru performs code-reviews and will suggest changes to improve the quality of code. It can show visual code profiles (show the internals of your code) to pinpoint performance.
- **Amazon Lex** 
    - is a conversion interface service. 
    - With Lex you can build voice and text chatbots
- **Amazon Personalize** 
    - is a real-time recommendations service. 
    - Same technology used to make product recommendations to customers shopping on the Amazon platform
- **Amazon Polly** 
    - is a text-to-speech service. 
    - Upload your text and an audio file spoken by synthesized voice is generated.
- **Amazon Rekognition** 
    - is image and video recognition service. 
    - Analyze images and videos to detect and label objects, people, celebrities.
- **Amazon Transcribe** 
    - is a speech-to-text service. 
    - Upload your audio file and it is converted
- **Amazon Textract** and OCR (extract text from scanned documents) service. 
    - When you have paper forms and you want to digitally extract the data.
- **Amazon Translate** 
    - neural machine learning translation service. 
    - Uses deep learning models to deliver more accurate and natural sounding translations.
- **Amazon Comprehend** 
    - is a Natural Language Processor (NLP) service. 
    - Find relationships between text to produce insights. Looks at data such as Customer emails, support tickets, social media and makes predictions.
- **Amazon Forecast** 
    - is a time-series forecasting service. 
    - Forecast business outcomes such as product demand, resource needs or financial performance.
- **AWS Deep Learning AMIs** 
    - Amazon EC2 instances pre-installed with popular deep learning frameworks and interfaces such as TensorFlow, PyTorch, Apache MXNet, Chainer, Gluon, Horovod, and Keras
- **AWS Deep Learning Containers** 
    - Docker images instances pre-install with popular deep learning frameworks and interfaces such as TensorFlow, PyTorch, and Apache MXNet.
- **AWS DeepComposer** 
    - is machine-learning enabled musical keyboard
- **AWS DeepLens** 
    - is a video-camera that uses deep-learning.
- **AWS DeepRacer** 
    - a toy race car that can be powered with machine-learning to perform autonomous driving.
- **Amazon Elastic Inference** 
    - allows you to attach low-cost GPU-powered acceleration to EC2 instances to reduce the cost of running deep learning inference by up to 75%.
- **Amazon Fraud Detector** 
    - is a fully managed fraud detection a service. 
    - identify potentially fraudulent online activities such as online payment fraud and the creation of fake accounts.
- **Amazon Kendra** 
    - enterprise machine learning search engine service. 
    - Uses natural language to suggest answers to question instead of just simple keyword matching
- **Amazon SageMaker** 
    - unified ML platform for building ML solutions end-to-end


# 3 BigData and Analytics Services
10:37:52 BigData and Analytics Services


**What is BigData?**
A term used to describe massive volumes of structured/unstructured data that is so large it is difficult to move and process using traditional database and software techniques.

--- 
- **Amazon Athena** 
    - is a serverless interactive query service. 
    - It can take a bunch of CSV or JSON files in an S3 Bucket and load them into temporary SQL tables so you can run SQL queries. When you want to query CSV or JSON files
- **Amazon CloudSearch** 
    - is a fully managed full-text search service. 
    - When you want to add search to your website
- **Amazon Elasticsearch Service (ES)** 
    - is a managed Elasticsearch cluster. 
    - Elasticsearch is an open-source full-text search engine. It is more robust than CloudSearch but requires more server and operational maintenance.
- **Amazon Elastic MapReduce (EMR)** 
    - is for data processing and analysis. 
    - It can be used for creating reports just like Redshift but is more suited when you need to transform unstructured data into structured data on the fly.
- **Kinesis Data Streams** 
    - is a real-time streaming data service. 
    - Create Producers which send data to a stream. Multiple Consumers can consume data within a stream. Use for real-time analytics, clickstreams, ingesting data from a fleet of IoT Devices
- **Kinesis Firehose** 
    - is serverless and a simpler version of Data Streams, 
    - You pay on-demand based on how much data is consumed through the stream and you don’t worry about the underlying servers.
- **Amazon Kinesis Data Analytics** 
    - allows you to run queries against data that is flowing through your real-time stream so you can create reports and analysis on emerging data.
- **Amazon Kinesis Video Streams** 
    - allows you to analyze or apply processing on real-time streaming video.
- **Managed Kafka Service (MSK)** 
    - a fully managed Apache Kafka service. 
    - Kafka is an open-source platform for building real-time streaming data pipelines and applications. It is similar to Kinesis but with more robust functionalities
- **Redshift** 
    - is a petabyte-size data-warehouse. Data-warehouses are for Online Analytical Processing (OLAP ) 
    - Data-warehouses can be expensive because they are keeping data “hot”. Meaning that we can run a very complex query and a large amount of data and get that data back very fast. When you want to quickly generate analytics or reports from a large amount of data.
- **Amazon QuickSight** 
    - is a business intelligence (BI) dashboard. 
    - You can use it to create business dashboards to power business decisions. It requires little to no programming knowledge, connects and ingests to many different types of databases
- **AWS Data Pipeline** 
    - automates the movement of data. You can reliably move data between compute and storage services.
- **AWS Glue** 胶 粘合
    - is an Extract, Transform, Load (ETL) service. 
    - Moving data from one location to another and where you need to perform transformations before the final destination. 
    - Similar to Database Migration Service (DMS) but more robust
- **AWS Lake Formation** 
    - is a centralized, curated, and secured repository that stores all your data. 
    - A data lake is a storage repository that holds a vast amount of raw data in its native format until it is needed.
- **AWS Data Exchange** 
    - is a catalog of third-party datasets. 
    - You can download for free subscribe or purchase datasets. Eg. COVID-19 Foot Traffic Data, IMDB TV and Movie data, Historical Weather Data

# 4 Amazon QuickSight (视觉化显示数据)
10:42:11 Amazon QuickSight

**Amazon QuickSight** is a **Business Intelligence (BI) Dashboard** that allows you to ingest data from various AWS storage or database services to **quickly visualize business data** with minimal programming or data formula knowledge.
用来 视觉化显示数据
![](image/Pasted%20image%2020230521132936.png)


QuickSight uses **SPICE** (super-fast, parallel, in-memory, calculation engine) to achieve blazing fast performance at scale

**Amazon QuickSight ML Insights** – Detect Anomalies, Perform accurate forecasting, Generate Natural Language Narratives.
**Amazon QuickSight Q** - Ask questions using natural language, on all your data, and receive answers in seconds.

## 4.1 QuickSight Follow Along
10:43:26 QuickSight Follow Along

需要先 create QuickSight Account

![](image/Pasted%20image%2020230521133204.png)

![](image/Pasted%20image%2020230521133225.png)


新产生 quickSight 中  会有一些 sample

![](image/Pasted%20image%2020230521133458.png)

create dataset
![](image/Pasted%20image%2020230521133552.png)


上传了这个 file 带 quickset 中, 根据这其中多个数据 图形化显示 

![](image/Pasted%20image%2020230521133855.png)


delete 这个 quicksight account
![](image/Pasted%20image%2020230521133946.png)

![](image/Pasted%20image%2020230521134043.png)
