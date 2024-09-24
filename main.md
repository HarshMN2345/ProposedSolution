# Application Documentation: Efficient Querying of Structured Databases

## Problem Statement

Many Businesses relys on structured data stored in Excel sheets for various operations. However, querying such data can be inefficient, especially when it needs to be transferred between formats like Excel and MongoDB. Traditional methods lack flexibility and scalability, and there’s a need for an automated system that can process and query Excel-based structured data effectively.

### Key Challenges:
- Manual uploading and processing of Excel sheets is time-consuming.
- Inconsistent queries can result from natural language processing (NLP) methods translating user queries to MongoDB query language.
- There's no standardized method for repeatedly asking similar questions across multiple datasets.

## Flow Diagram:

1. **Data Ingestion**: Excel sheets are uploaded to the system.
2. **Data Processing**: The system processes the Excel data into a structured format suitable for querying.
3. **Query Translation**: The system translates user queries into MongoDB query language.
4. **Query Execution**: The system executes the translated query on the processed data.
5. **Result Retrieval**: The system retrieves the results of the query and presents them to the user.

![Description of the image](/IMAGES/flow.jpg)

## Proposed Solution

The ideal solution involves:
- A system to automate the upload and querying of Excel data.
- A web application with a structured format for querying datasets, such as based on HS codes or months.
- A mechanism to save and reuse specific queries for consistent outputs.
- The ability to handle similar queries across multiple Excel sheets in a standardized way.
- An API to handle uploads and queries directly through the web interface.

---
## Our Solution

### Current Implementation

#### Data Upload:
- We have created a script (`mongo.py`) using the **pymongo** library to directly upload Excel sheet data to a MongoDB collection.
- This script processes the Excel files and uploads them into a specified collection within MongoDB.

#### Querying Mechanism:
- We are leveraging **MongoDB’s aggregation pipeline** and query features (using MongoDB Compass for generating queries).
- The current system allows users to upload Excel data and query based on predefined categories, such as HS codes or months.

![Description of the image](/IMAGES/image.png)

#### Challenges:
- NLP-generated MongoDB queries are inconsistent across different questions, making it difficult to reuse queries.
- To address this, we plan to standardize a set of common questions. We will create and store aggregation pipelines that will run every time a user asks one of these questions, ensuring consistent results.
- The system will hardcode query structures to fit specific formats like HS codes or months for more reliable outputs.

---

### Future Scope

#### API Integration:
- We plan to replace the current script with an API that handles file uploads via the web interface. When a file is uploaded, a POST request will be sent to the server, triggering the upload and storage process in MongoDB.

#### Enhanced Query Mechanism:
- **Pandas AI** can be introduced to provide agents for handling queries more dynamically, making querying more efficient and automated.

#### Standardization of Queries:
- The web application will provide a set of standardized questions that users can ask. These will be tailored to the format of the Excel sheets, ensuring that the same format can be queried efficiently.
- Users will be able to select predefined questions for consistent results across different datasets.
