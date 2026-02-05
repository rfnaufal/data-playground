## Biglake

**Preparation :**
1. Activate Cloud Shell

   List the active account name `gcloud auth list`

   List the project ID : `gcloud config list project`

    <img src="ss/datastream/01.png" width=75%>

#### Task 1. Create a connection resource

1. From the Navigation Menu, go to BigQuery > Studio. Click Done.

2. To create a connection, switch to Explorer tab and click + Add data. Then use the search bar for data sources to search for Vertex AI. Click on the result for Vertex AI.

3. In the Access external data in place, select BigQuery Federation.

4. In the Connection type list, select Vertex AI remote models, remote functions and BigLake (Cloud Resource).

5. In the Connection ID field, type my-connection.

6. For Location type, choose Multi-region and select US (multiple regions in United States) from dropdown.

7. Click Create connection.

#### Task 2. Set up access to a Cloud Storage data lake

#### Task 3. Create a BigLake table

**Create Dataset**

**Create the table**

#### Task 4. Query a BigLake table through BigQuery

#### Task 5. Set up access control policies

**Verify the column level security**

```sql
SELECT * FROM `Project ID.demo_dataset.biglake_table`
```