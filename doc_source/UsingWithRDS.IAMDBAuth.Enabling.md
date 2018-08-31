# Enabling and Disabling IAM Database Authentication<a name="UsingWithRDS.IAMDBAuth.Enabling"></a>

By default, IAM database authentication is disabled on DB clusters\. You can enable IAM database authentication \(or disable it again\) using the AWS Management Console, AWS CLI, or the Amazon RDS API\.

**Topics**
+ [AWS Management Console](#UsingWithRDS.IAMDBAuth.Enabling.Console)
+ [AWS CLI](#UsingWithRDS.IAMDBAuth.Enabling.CLI)
+ [API](#UsingWithRDS.IAMDBAuth.Enabling.API)

## AWS Management Console<a name="UsingWithRDS.IAMDBAuth.Enabling.Console"></a>

To create a new DB cluster with IAM authentication by using the console, see [Creating an Amazon Aurora DB Cluster](Aurora.CreateInstance.md)\.

Each of these creation workflows has a **Configure Advanced Settings** page, where you can enable IAM DB authentication\. In that page's **Database Options** section, choose **Yes** for **Enable IAM DB Authentication**\.

**To enable or disable IAM authentication for an existing DB cluster**

1. Open the Amazon RDS console at [https://console\.aws\.amazon\.com/rds/](https://console.aws.amazon.com/rds/)\.

1. In the navigation pane, choose **Clusters**\.

1. Choose the DB cluster that you want to modify\.

1. Choose **Cluster actions**, and then choose **Modify cluster**\.

1. In the **Database options** section, for **IAM DB authentication**, choose **Enable IAM DB authentication** or **Disable**, and then choose **Continue**\.

1. To apply the changes immediately, choose **Apply immediately**\.

1. Choose **Modify cluster**\.

**To restore a DB cluster**

1. Open the Amazon RDS console at [https://console\.aws\.amazon\.com/rds/](https://console.aws.amazon.com/rds/)\.

1. In the navigation pane, choose **Snapshots**\.

1. Choose the snapshot you want to restore, and then choose **Restore Snapshot** from **Snapshot Actions**\.

1. In the **Settings** section, type an identifier for the DB instance in **DB Instance Identifier**\.

1. In the **Database options** section, for **IAM DB authentication**, choose **Enable IAM DB authentication** or **Disable**\.

1. Choose **Restore DB Instance**\.

## AWS CLI<a name="UsingWithRDS.IAMDBAuth.Enabling.CLI"></a>

To create a new DB cluster with IAM authentication by using the AWS CLI, use the following command:
+ [http://docs.aws.amazon.com/cli/latest/reference/rds/create-db-cluster.html](http://docs.aws.amazon.com/cli/latest/reference/rds/create-db-cluster.html)

Specify the `--enable-iam-database-authentication` option\.

For an existing DB cluster, use one of the following AWS CLI command:
+ [http://docs.aws.amazon.com/cli/latest/reference/rds/modify-db-cluster.html](http://docs.aws.amazon.com/cli/latest/reference/rds/modify-db-cluster.html)

Specify either the `--enable-iam-database-authentication` or `--no-enable-iam-database-authentication` option, as appropriate\. 

By default, Amazon RDS performs the modification during the next maintenance window\. If you want to override this and enable IAM DB authentication as soon as possible, use the `--apply-immediately` parameter\. 

If you are restoring a DB cluster, use one of the following AWS CLI commands:
+ `[restore\-db\-cluster\-to\-point\-in\-time](http://docs.aws.amazon.com/cli/latest/reference/rds/restore-db-cluster-to-point-in-time.html)`
+ `[restore\-db\-cluster\-from\-db\-snapshot](http://docs.aws.amazon.com/cli/latest/reference/rds/restore-db-instance-from-db-snapshot.html)`

The IAM database authentication setting defaults to that of the source snapshot\. To change this setting, set the `--enable-iam-database-authentication` or `--no-enable-iam-database-authentication` option, as appropriate\.

## API<a name="UsingWithRDS.IAMDBAuth.Enabling.API"></a>

For a new DB cluster, use the following API action:
+ [http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_CreateDBCluster.html](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_CreateDBCluster.html)

Set the `EnableIAMDatabaseAuthentication` parameter to `true`\.

For an existing DB cluster, use the following API action:
+ [http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_ModifyDBCluster.html](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_ModifyDBCluster.html)

Set the `EnableIAMDatabaseAuthentication` to `true` to enable IAM authentication, or `false` to disable it\.

If you are restoring a DB cluster, use one of the following API actions:
+ [RestoreDBClusterToPointInTime](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_RestoreDBClusterToPointInTime.html)
+ [RestoreDBClusterFromSnapshot](http://docs.aws.amazon.com/AmazonRDS/latest/APIReference/API_RestoreDBClusterFromSnapshot.html)

The IAM database authentication setting defaults to that of the source snapshot\. To change this setting, set the `EnableIAMDatabaseAuthentication` to `true` to enable IAM authentication, or `false` to disable it\.