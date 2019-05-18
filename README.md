# NZ Tech Week 2019 - Analytics on AWS

## Preparation

### Choose an S3 Bucket Prefix
During this lab, you will create a number of S3 buckets. Because S3 bucket names need to be globally unique, you should now choose a bucket name prefix based upon your name or email address. For example, `craigr-amazon`. Make a note of your choice. These instructions will subsequently refer to this prefix as `{MyS3Prefix}`. For example, suppose you chose `saraq-edu-nz` as your prefix, and the instructions say to create an S3 bucket called `{S3Prefix}-stations`. Then you should create a bucket called `saraq-edu-nz-stations`.

## Let's Go

- Login in AWS Console

- Switch region in toolbar to *N. Virginia* (us-east-1)

- Click *Services* in toolbar, then Select *Glue*

- Click *Databases* in sidebar (under *Data catalog*)

- Click *Add database* button.

- Type `ghcnlab` as the database name.
