# NZ Tech Week 2019 - Analytics on AWS

## Preparation

### Choose an S3 Bucket Prefix
During this lab, you will create a number of S3 buckets. Because S3 bucket names need to be globally unique, you should now choose a bucket name prefix based upon your name or email address. For example, `craigr-amazon`. Make a note of your choice. These instructions will subsequently refer to this prefix as `{MyS3Prefix}`. For example, suppose you chose `saraq-edu-nz` as your prefix, and the instructions say to create an S3 bucket called `{S3Prefix}-stations`. Then you should create a bucket called `saraq-edu-nz-stations`.

## Let's Go

- Login in AWS Console

- Switch region in toolbar to *N. Virginia* (us-east-1)

- Click *Services* in toolbar, then Select *Glue*

- Click *Databases* in the sidebar (under *Data catalog*)

- Click *Add database* button.

- Type `ghcnlab` as the *Database name*. Leave the *Location* empty, and enter your choice of *Description*. Then click the *Create* button. You should now see the `ghcnlab` database listed.

- Click *Tables* in the sidebar (under *Data catalog* / *Tables*).

- Click the *Add tables* drop-down menu, and select *Add table manually*. A table creation wizard will appear.

- Type `allyears` as the *Table name*. Select `ghcnlab` as the *Database*. Enter something like `Observations for all stations, years and elements` in the *Description*. Click *Next*.

**Important:** This is where we reference the NOAA GHCN observations published in the AWS Registry of Open Data

- On the *Add a data store* page, locate the *Data is located in* radio buttons, and select *Specified path in another account*. Then under *Include path*, enter this URL: `s3://noaa-ghcn-pds/csv/`. Then click *Next*.

> We are telling the AWS Glue service that source data for the table is in an S3 bucket owned by NOAA, but with the standard access policy modified so that it's shared with the world.

- On the *Choose a data format* page, locate the *Classification* radio buttons, and select the *CSV* option. You will be prompted for a *Delimter*. Select *Comma* from the drop-down. Then click *Next*.

> We are telling AWS Glue what format NOAA is using. Glue can automatically discover this for itself using a Crawler, but we're do this manually in the lab.

- On the *Define a schema* page, click the *Add column* button. An *Add column* dialogue will pop up. Type `stationid` in the *Column name* field. The *Column type* is *string*. Leave *Partition key* unchecked. Let the *Column number* default. Click the *Add* button. You will see the new column listed on the schema page.

- Click the *Add column* button again. We're going to add several more columns. All have a *Column type* of *string*. Here is the full list of the column names:
  - stationid
  - ymd
  - element
  - datum
  - m_flag
  - q_flag
  - s_flag
  - obs_time

- You will see the list of 8 columns on the schema page. Click *Next*.

- The final step in the wizard is the *Review* page. Review the settings, then click the *Finish* button. You will now return to the list of tables in the Glue Data Catalog. If you click on the `allyears` table name, you'll see ![allyears](./screenshots/Glue-Schema-allyears.png):

