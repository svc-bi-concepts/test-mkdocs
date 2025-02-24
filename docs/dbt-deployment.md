# dbt Deployment & Documentation

## Introduction

Deploying dbt models effectively ensures that transformations run on a **scheduled basis**, providing fresh and reliable data to downstream analytics.  
Additionally, **documentation** serves as a **single source of truth**, helping teams understand **data lineage, model definitions, and test coverage**.

---

## 1. Setting Up a Production Deployment in dbt Cloud

To ensure **automated and consistent transformations**, we set up a **deployment job** in dbt Cloud.

### **Steps to Create a Deployment Job**
1. **Go to dbt Cloud** → Click on **"Deploy"** in the navigation menu.
2. **Create a New Job** by selecting **+ Create Job**.
3. **Configure the Job Settings:**
   - **Job Name**: `Production Deployment`
   - **Environment**: `Production`
   - **Schedule**: Set up a cron schedule (e.g., `0 6 * * *` for daily 6 AM runs).
   - **Commands to Run**:
     ```sh
     dbt run
     dbt test
     ```
   - **Threads**: Ensure **parallel execution** for faster runs.

4. **Save & Run** the job.

   ![dbt Deployment Job](./assets/screenshots/dbtDeployment/dbtDeployment1.png)

✅ **Now, dbt Cloud will execute transformations automatically based on the schedule.**

---

## 2. Creating Documentation for dbt Models

Documentation in dbt helps **explain models, columns, and transformations** to stakeholders.

### **Defining Documentation in `schema.yml`**
```yaml
models:
  - name: stg_orders
    description: "Staging model for orders"
    columns:
      - name: order_id
        description: "Unique identifier for each order."
        tests:
          - unique
          - not_null
      - name: order_total
        description: "Total order amount in USD."
        tests:
          - not_null
          - dbt_utils.accepted_range:
              min_value: 0
```
✅ **Every model and column now has clear documentation** for analysts and engineers.

---

## 3. Generating and Serving Documentation

Once documentation is written, we can **generate an interactive website** for our dbt project.

### **Generate dbt Docs Locally**
```sh
dbt docs generate
```
This command:
- Parses all `schema.yml` files.
- Builds a **data catalog** with descriptions and tests.
- Generates an HTML-based UI for easy exploration.

### **Serve Documentation in a Local Web Browser**
```sh
dbt docs serve
```
- Opens an interactive **data lineage graph**.
- Provides a UI for **browsing model descriptions**.

   ![dbt Docs UI](./assets/screenshots/dbtDeployment/dbtDeployment2.png)

---

## 4. Automating Documentation Updates in dbt Cloud

To keep documentation up-to-date in **dbt Cloud**:

1. **Navigate to dbt Cloud → Deploy → Jobs**
2. **Create a new job** with the following commands:
   ```sh
   dbt docs generate
   ```
3. **Save & Schedule** the job to run **after each transformation**.

---

## 5. Setting Up a Production Environment

A production environment ensures that **only tested, validated models** are exposed to analysts.

### **Steps to Set Up a Production Environment**
1. **Go to dbt Cloud** → Click **Environments**.
2. **Create a New Environment**:
   - **Name**: `Production`
   - **Warehouse Size**: `Medium` (or appropriate)
   - **Threads**: `16` (for faster parallel execution)

3. **Associate this environment** with the **Production Deployment Job**.

---

## 🎉 Next Steps

Your dbt project is now **automated, tested, and documented**!  
Proceed to **building dashboards** with your transformed data.

🔗 **Continue to:** [Building Dashboards with Snowflake](data-visualization.md)