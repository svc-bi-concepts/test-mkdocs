# dbt Cloud Setup

## 1. Create a dbt Cloud Account
To start using dbt Cloud, sign up for an account on the [dbt Cloud website](https://cloud.getdbt.com/){:target="_blank"}.

1. Navigate to the signup page.
2. Choose the free plan (or a trial of the Team/Enterprise plan if needed).
3. Complete the registration process.

📸 *Insert screenshot of the dbt Cloud signup page here.*

---

## 2. Set Up a New Project
Once logged in, create a new project:

1. Click on **"New Project"**.
2. Select your data warehouse (Snowflake).
3. Follow the guided setup wizard.

📸 *Insert screenshot of the "New Project" setup page here.*

---

## 3. Connect dbt Cloud to Snowflake
To enable dbt transformations, you need to link dbt Cloud to your Snowflake instance:

1. Choose **Snowflake** as your data warehouse.
2. Enter the required Snowflake credentials:
   - Account name
   - Username
   - Password (or authentication method like OAuth)
   - Warehouse, Database, and Schema
3. Test the connection and save.

📸 *Insert screenshot of Snowflake connection settings in dbt Cloud.*

---

## 4. Configure the Project Repository
If you plan to use version control:

1. Connect your **GitHub/Bitbucket/GitLab** repository.
2. Authorize dbt Cloud to access your repository.
3. Select the correct repository and branch.

📸 *Insert screenshot of repository configuration settings.*

---

## 5. Verify Setup and Run a Test
To confirm everything is set up correctly:

1. Click **"Develop"** to open the dbt IDE.
2. Run `dbt debug` to validate the connection.
3. Execute `dbt run` to test a transformation.

📸 *Insert screenshot of dbt run results.*

---

## 🎉 Next Steps
Now that dbt Cloud is configured, proceed to setting up transformations and version control.

🔗 **Continue to:** [Data Transformation with dbt](dbt-transformation.md)