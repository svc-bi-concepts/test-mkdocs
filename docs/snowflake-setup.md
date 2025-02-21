# Snowflake Account Setup

This section walks you through setting up a Snowflake account, creating the necessary databases, and configuring the environment for the hands-on lab.

## 1. Creating a Snowflake Account

To get started, sign up for a free **Snowflake Trial**.

1. Visit the [Snowflake Sign-Up Page](https://signup.snowflake.com/){:target="_blank"}.
2. Choose your preferred cloud provider (AWS, Azure, or GCP).
3. Enter your details and complete the registration.
4. Check your email and follow the activation link.

📌[Snowflake Sign-Up Page](assets/images/snowflake_signup.png)

---

## 2. Configuring Snowflake

Once your account is activated, log in to the **Snowflake UI**.

1. Go to the Snowflake URL provided in the confirmation email.
2. Enter your credentials and log in.
3. The Snowflake **Home Page** will load.

📌[Snowflake Login Page](assets/images/snowflake_login.png)

---

## 3. Navigating Snowflake

Before creating databases, let’s explore the **Snowflake UI**.

- **Databases** → Where data is stored.
- **Warehouses** → Compute resources for queries.
- **Worksheets** → SQL execution environment.

📌[Snowflake UI Overview](assets/images/snowflake_ui_overview.png)

---

## 4. Creating Databases

For this hands-on lab, we need two databases:
- **PSA** (Persistent Staging Area)
- **ANALYTICS** (Final Data Warehouse)

Run the following SQL to create them:

```sql
CREATE DATABASE PSA;
CREATE DATABASE ANALYTICS;
```

📌[Creating a Database in Snowflake](assets/images/snowflake_create_db.png)

---

## 5. Compute Warehouse Setup

Snowflake uses **virtual warehouses** to process queries. Create a warehouse for this lab:

```sql
CREATE WAREHOUSE TRANSFORMER
WITH WAREHOUSE_SIZE = 'XSMALL'
AUTO_SUSPEND = 60
AUTO_RESUME = TRUE
INITIALLY_SUSPENDED = TRUE;
```

This ensures:

 **Cost Efficiency** → Auto-suspends when not in use.  
 **Performance** → Automatically resumes when queries are executed.

📌[Creating a Warehouse in Snowflake](assets/images/snowflake_create_wh.png)

## 6. Retrieving Snowflake Account Details

To integrate Snowflake with **Fivetran** and **dbt**, we need specific account details.

1. **Account URL**: This is the URL you use to log in to Snowflake.
2. **Account Name**: Found in the Snowflake UI under the profile section.
3. **Warehouse Name**: The name of the warehouse you created (e.g., `TRANSFORMER`).
4. **Database Names**: The names of the databases you created (e.g., `PSA`, `ANALYTICS`).

📌[Snowflake Account Details](assets/images/snowflake_account_details.png)

Run the following SQL to retrieve the account name and other details:

```sql
SELECT CURRENT_ACCOUNT() AS ACCOUNT_NAME,
    CURRENT_REGION() AS REGION,
    CURRENT_ROLE() AS ROLE,
    CURRENT_WAREHOUSE() AS WAREHOUSE,
    CURRENT_DATABASE() AS DATABASE;
```

Make sure to note down these details as they will be required for the next steps in setting up Fivetran and dbt.


## 7. Download Login Details Template

To keep track of your login details for Snowflake, Fivetran, and dbt, download and fill out the following template:

📄 [Download Login Details Template](assets/templates/login_details_template.txt){:download}

This template includes sections for:
- **Snowflake Account Details**
- **Fivetran Account Details**
- **dbt Account Details**

Make sure to save this file securely and update it as needed.


---

## Next Steps

Now that we have **databases** and a **warehouse** set up, we are ready to move on to **data ingestion with Fivetran**.

📌 **Continue to the next section: [Fivetran Setup](fivetran-setup.md)** 🚀