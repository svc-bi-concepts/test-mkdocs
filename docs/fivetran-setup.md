# Fivetran Setup

## 1. Create a Fivetran Account
Fivetran is a cloud-based data integration platform that enables automated data ingestion from various sources.

1. To start using Fivetran, sign up for an account on the [Fivetran website](https://go.fivetran.com/signup/free-trial-emea/){:target="_blank"}.

2. Fill in your credentials and sign up.

    ![Fivetran Email Verification](./assets/screenshots/ftSetup/ftSetup1.png)

    ![Fivetran Email Verification](./assets/screenshots/ftSetup/ftSetup2.png)

3. Verify your email via the confirmation link you received in your inbox - **Verify my email**.

    ![Fivetran Email Verification](./assets/screenshots/ftSetup/ftSetup3.png)

4. After email verification, complete the form with your username and password. Also, agree to Fivetran's terms and conditions. Click **Get Started**.

    ![Fivetran Email Verification](./assets/screenshots/ftSetup/ftSetup4.png)

    ![Fivetran Email Verification](./assets/screenshots/ftSetup/ftSetup5.png)

5. Skip the next step.

    ![Fivetran Email Verification](./assets/screenshots/ftSetup/ftSetup6.png)


---

## 2. Setup a Google Drive Connector
Fivetran enables automated data ingestion from Google Drive.

1. Select **Google Drive** as your data source. You have to select now three connectors you are interested in, please add the Google Drive connector. For the residual two, feel free to choose any connector.

    ![Fivetran Connector Selection](./assets/screenshots/ftSetup/ftSetup7.png)


    Click **Next**.


2. Select or search for Google Drive.

    ![Fivetran Connector Selection](./assets/screenshots/ftSetup/ftSetup8.png)

    Let's first set up our connector.

    ![Select connector](./assets/screenshots/ftSetup/ftSetup9.png)

3. Fill out the connector requirements (find here the docs for the [Google Drive connector](https://fivetran.com/docs/connectors/files/google-drive/setup-guide)):

    - **Destination schema**: ```jaffle_shop```
    - **Folder URL**: ```https://drive.google.com/drive/u/0/folders/1Z_U_6SVP6vWXGJWHu9Fl_uUjieyVjaWX```
    

    Desired state:

    ![Google Drive Connection](./assets/screenshots/ftSetup/ftSetup10.png)

    **Save & Test** the connector.

4. Click **Save & Test** to verify the connection.

    ![Google Drive Connection](./assets/screenshots/ftSetup/ftSetup11.png)

    Click **Continue**.

Connector configuration is set up - go to the next step and add Snowflake as our destination.

---

## 3. Configure Snowflake as the Destination
1. Select **Destinations** to connect Fivetran with Snowflake.

    ![Fivetran Connector Selection](./assets/screenshots/ftSetup/ftSetup12.png)

    **Add destination**.

    ![Fivetran Connector Selection](./assets/screenshots/ftSetup/ftSetup13.png)

    Select **Snowflake**.

    ![Snowflake Connection](./assets/screenshots/ftSetup/ftSetup14.png)

2. Fill in the required information (Connection details from Snowflake and additional Fivetran configuration):
    - **Snowflake Account URL** (example: Snowfakes Account/Server URL `<org_name>-<account_name>.snowflakecomputing.com/` | `BYELBTA-MV59868.snowflakecomputing.com`)
    - **Snowflake USER**: `<username>`
    - **Database**: `PSA`
    - **Auth**: set to `PASSWORD`
    - **Role**: `ACCOUNTADMIN`
    - **Password**: `<password>`
    - **Data processing location**: `EU`
    - **Fivetran processing cloud provider**: `AWS`
    - **Time Zone**: `UTC`

    Desired state:

    ![Snowflake Connection](./assets/screenshots/ftSetup/ftSetup15.png)

    - Click **Save & Test**.


    
    - **All connection tests passed!**

    ![Snowflake Connection](./assets/screenshots/ftSetup/ftSetup16.png)


3. **View Destination** and in the top right, select **View** for the `jaffle_shop`.

    ![Snowflake Connection](./assets/screenshots/ftSetup/ftSetup17.png)


    ![Snowflake Connection](./assets/screenshots/ftSetup/ftSetup18.png)



---

## 4. Perform Initial Data Sync
Once connected, start syncing data from **Google Drive to Snowflake**.

1. Click **Start Initial Sync**.

    ![Initial Sync](./assets/screenshots/ftSetup/ftSetup19.png)


2. Monitor progress in the Fivetran dashboard by refreshing the browser from time to time (duration ~1 min).

    ![Snowflake Data](./assets/screenshots/ftSetup/ftSetup20.png)

    On hover, you can see the details of the load process.

    ![Snowflake Data](./assets/screenshots/ftSetup/ftSetup21.png)


3. Once complete, verify that data is ingested into **Snowflake** under the `PSA` (Persistent Staging Area) database.

    ![Snowflake Data](./assets/screenshots/ftSetup/ftSetup22.png)

!!! note "Disable Fivetran Sync"
    Feel free to turn off the sync on the top right corner. ``ENABLED`` should be switched to ``PAUSED``.

    ![Snowflake Data](./assets/screenshots/ftSetup/ftSetup23.png)

    ![Snowflake Data](./assets/screenshots/ftSetup/ftSetup24.png)





---


## 5. What we have achieved so far:

<div class="grid cards" markdown>

-   :material-database-check:{ .lg .middle } __Snowflake Ready__

    ---

    - ✅ Snowflake account configured  
    - ✅ Two databases created (ANALYTICS, PSA)  


-   :material-code-tags-check:{ .lg .middle } __dbt Cloud Connected__

    ---

    - ✅ dbt Cloud set up  
    - ✅ Connected to Snowflake  



-   :material-link-variant-plus:{ .lg .middle } __Fivetran Integrated__

    ---

    - ✅ Fivetran account created  
    - ✅ Connected to Snowflake  



-   :material-pipe:{ .lg .middle } __Pipeline Running__

    ---

    - ✅ Fivetran syncing data from Google Drive  
    - ✅ Google Sheets loaded into **jaffle_shop** schema 



</div>

---

## 🚀 Let's take a quick walk through the UI


## 🎉 Next Steps
Now that Fivetran is successfully pulling data into Snowflake, proceed to **dbt transformations**.

🔗 **Continue to:** [Data Integration with dbt](dbt-transformation.md)