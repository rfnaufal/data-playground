## SQL Workflow in Dataform

In this lab, I created and executed a SQL workflow in Dataform to load data into BigQuery.

#### Task 1. Create a Dataform repository

1. From the Navigation Menu, go to **BigQuery > Dataform**.
2. In the **Repository ID** field, enter `quickstart-repository`.
3. In the **Region** list, select `us-east1`, then click **Create**.

<img src="ss/dataform/01.png" width=60%> <br>

<img src="ss/dataform/02.png" width=60%>

#### Task 2. Create and initialize a Dataform development workspace.

On the Dataform page, click the `quickstart-repository` repository that was just created.

Click **Create Development Workspace**.

In the **Create development workspace** window:

- In the **Workspace ID** field, enter `quickstart-workspace`.

<img src="ss/dataform/03.png" width="60%"><br>

Once the workspace was created, click the `quickstart-workspace` development workspace and then click **Initialize Workspace**.

<img src="ss/dataform/04.png" width="60%">

#### Task 3. Create and execute a SQL workflow.

**Create a SQLX file for defining a view**

<img src="ss/dataform/05.png" width=60%>

Enter the following code: 

```sql
config {
  type: "view"
}

SELECT
  "apples" AS fruit,
  2 AS count
UNION ALL
SELECT
  "oranges" AS fruit,
  5 AS count
UNION ALL
SELECT
  "pears" AS fruit,
  1 AS count
UNION ALL
SELECT
  "bananas" AS fruit,
  0 AS count

```

**Create a SQLX file for table definition**

Create another SQLX file to define a table based on the view.

<img src="ss/dataform/06.png" width=60%>

#### Task 4. Grant Dataform access to BigQuery

Grant the required permissions so Dataform can create and manage objects in BigQuery.


<img src="ss/dataform/07.png" width=60%>

#### Task 5. Execute the workflow

Once everything was configured, I executed the workflow.

<img src="ss/dataform/08.png" width=60%> <br>

<img src="ss/dataform/09.png" width=60%>

## Lesson Learned

One important thing I missed during this lab was **initializing the development workspace**.

When the workspace is not initialized:
- The **Execute** button is greyed out
- The workflow cannot be run

After recreate workspace and click **Initialize workspace**, the execution option becomes available and the workflow runs successfully.

**Takeaway:** Initializing the Dataform workspace is required before executing any workflows.