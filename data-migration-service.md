#### Database Migration Service (DMS)
Database Migration Service (DMS) can migrate your data to and from the most widely used commercial and open-source databases such as Oracle, PostgreSQL, Microsoft SQL Server, Amazon Redshift, MariaDB, Amazon Aurora, MySQL, and SAP Adaptive Server Enterprise (ASE). The service supports homogeneous migrations such as Oracle to Oracle, as well as heterogeneous migrations between different database platforms, such as Oracle to MySQL or SQL Server to PostgreSQL.

#### Python Code
```python
import boto3

client = boto3.client('dms')
```

#### These are the available methods:

* [add_tags_to_resource()](#add_tags_to_resource)
* [create_endpoint()](#create_endpoint)
* [create_event_subscription()](#create_event_subscription)
* [create_replication_instance()](#create_replication_instance)
* [create_replication_task()](#create_replication_task)
* [reboot_replication_instance()](#reboot_replication_instance)
* [refresh_schemas()](#refresh_schemas)
* [reload_tables()](#reload_tabl* [es))
* [start_replication_task()](#](#es))
* [start_replication_task()])s* [tart_replication_task)
* [start_replica](#tart_replication_task)
* [start_repli)t* [ion_task_assessment()](](#ion_task_assessment())#* [start_replication](#start_replicati)_task_assessment)
* [start_replication_task_assessment_run()](#start_replication_task_assessment_run)
* [stop_replication_task()](#stop_replication_task)
* [test_connection()](#test_connection)

#### add_tags_to_resource
Adds metadata tags to an DMS resource, including replication instance, endpoint, security group, and migration task. These tags can also be used with cost allocation reporting to track cost associated with DMS resources, or used in a Condition statement in an IAM policy for DMS
```python
response = client.add_tags_to_resource(
    ResourceArn='string',
    Tags=[
        {
            'Key': 'string',
            'Value': 'string'
        },
    ]
)
```
- ResourceArn: Amazon Resource Name (ARN).
- Tags: A user-defined key-value pair that describes metadata added to an DMS resource
- key: A key is the required name of the tag(1-128 Unicode characters in length and can't be prefixed with "aws:" or "dms:")
- value: A value is the optional value of the tag. (1-256 Unicode characters in length and can't be prefixed with "aws:" or "dms:")
- Returns: {} type (dict)
- Exception: DatabaseMigrationService.Client.exceptions.ResourceNotFoundFault

**Example**
```python
response = client.add_tags_to_resource(
    # Required. Use the ARN of the resource you want to tag.
    ResourceArn='arn:aws:dms:us-east-1:123456789012:endpoint:ASXWXJZLNWNT5HTWCGV2BUJQ7E',
    # Required. Use the Key/Value pair format.
    Tags=[
        {
            'Key': 'Acount',
            'Value': '1633456',
        },
    ],
)

print(response)
```
Expected Output
```python
{
    'ResponseMetadata': {
        '...': '...',
    },
}
```

#### create_endpoint
For a MySQL source or target endpoint, don't explicitly specify the database using the DatabaseName request parameter on the CreateEndpoint API call. Specifying DatabaseName when you create a MySQL endpoint replicates all the task tables to this single database. For MySQL endpoints, you specify the database only when you specify the schema in the table-mapping rules of the DMS task.

```
response = client.create_endpoint(
    EndpointIdentifier='string',
    EndpointType='source'|'target',
    EngineName='string',
    Username='string',
    Password='string',
    ServerName='string',
    Port=123,
    DatabaseName='string',
    ExtraConnectionAttributes='string',
    KmsKeyId='string',
    Tags=[
        {
            'Key': 'string',
            'Value': 'string'
        },
    ],
    CertificateArn='string',
    SslMode='none'|'require'|'verify-ca'|'verify-full',
    ServiceAccessRoleArn='string',
    ExternalTableDefinition='string',
    DynamoDbSettings={
        'ServiceAccessRoleArn': 'string'
    },
    S3Settings={
        'ServiceAccessRoleArn': 'string',
        'ExternalTableDefinition': 'string',
        'CsvRowDelimiter': 'string',
        'CsvDelimiter': 'string',
        'BucketFolder': 'string',
        'BucketName': 'string',
        'CompressionType': 'none'|'gzip',
        'EncryptionMode': 'sse-s3'|'sse-kms',
        'ServerSideEncryptionKmsKeyId': 'string',
        'DataFormat': 'csv'|'parquet',
        'EncodingType': 'plain'|'plain-dictionary'|'rle-dictionary',
        'DictPageSizeLimit': 123,
        'RowGroupLength': 123,
        'DataPageSize': 123,
        'ParquetVersion': 'parquet-1-0'|'parquet-2-0',
        'EnableStatistics': True|False,
        'IncludeOpForFullLoad': True|False,
        'CdcInsertsOnly': True|False,
        'TimestampColumnName': 'string',
        'ParquetTimestampInMillisecond': True|False,
        'CdcInsertsAndUpdates': True|False,
        'DatePartitionEnabled': True|False,
        'DatePartitionSequence': 'YYYYMMDD'|'YYYYMMDDHH'|'YYYYMM'|'MMYYYYDD'|'DDMMYYYY',
        'DatePartitionDelimiter': 'SLASH'|'UNDERSCORE'|'DASH'|'NONE',
        'UseCsvNoSupValue': True|False,
        'CsvNoSupValue': 'string',
        'PreserveTransactions': True|False,
        'CdcPath': 'string'
    },
    DmsTransferSettings={
        'ServiceAccessRoleArn': 'string',
        'BucketName': 'string'
    },
    MongoDbSettings={
        'Username': 'string',
        'Password': 'string',
        'ServerName': 'string',
        'Port': 123,
        'DatabaseName': 'string',
        'AuthType': 'no'|'password',
        'AuthMechanism': 'default'|'mongodb_cr'|'scram_sha_1',
        'NestingLevel': 'none'|'one',
        'ExtractDocId': 'string',
        'DocsToInvestigate': 'string',
        'AuthSource': 'string',
        'KmsKeyId': 'string',
        'SecretsManagerAccessRoleArn': 'string',
        'SecretsManagerSecretId': 'string'
    },
    KinesisSettings={
        'StreamArn': 'string',
        'MessageFormat': 'json'|'json-unformatted',
        'ServiceAccessRoleArn': 'string',
        'IncludeTransactionDetails': True|False,
        'IncludePartitionValue': True|False,
        'PartitionIncludeSchemaTable': True|False,
        'IncludeTableAlterOperations': True|False,
        'IncludeControlDetails': True|False,
        'IncludeNullAndEmpty': True|False,
        'NoHexPrefix': True|False
    },
    KafkaSettings={
        'Broker': 'string',
        'Topic': 'string',
        'MessageFormat': 'json'|'json-unformatted',
        'IncludeTransactionDetails': True|False,
        'IncludePartitionValue': True|False,
        'PartitionIncludeSchemaTable': True|False,
        'IncludeTableAlterOperations': True|False,
        'IncludeControlDetails': True|False,
        'MessageMaxBytes': 123,
        'IncludeNullAndEmpty': True|False,
        'SecurityProtocol': 'plaintext'|'ssl-authentication'|'ssl-encryption'|'sasl-ssl',
        'SslClientCertificateArn': 'string',
        'SslClientKeyArn': 'string',
        'SslClientKeyPassword': 'string',
        'SslCaCertificateArn': 'string',
        'SaslUsername': 'string',
        'SaslPassword': 'string',
        'NoHexPrefix': True|False
    },
    ElasticsearchSettings={
        'ServiceAccessRoleArn': 'string',
        'EndpointUri': 'string',
        'FullLoadErrorPercentage': 123,
        'ErrorRetryDuration': 123
    },
    NeptuneSettings={
        'ServiceAccessRoleArn': 'string',
        'S3BucketName': 'string',
        'S3BucketFolder': 'string',
        'ErrorRetryDuration': 123,
        'MaxFileSize': 123,
        'MaxRetryCount': 123,
        'IamAuthEnabled': True|False
    },
    RedshiftSettings={
        'AcceptAnyDate': True|False,
        'AfterConnectScript': 'string',
        'BucketFolder': 'string',
        'BucketName': 'string',
        'CaseSensitiveNames': True|False,
        'CompUpdate': True|False,
        'ConnectionTimeout': 123,
        'DatabaseName': 'string',
        'DateFormat': 'string',
        'EmptyAsNull': True|False,
        'EncryptionMode': 'sse-s3'|'sse-kms',
        'ExplicitIds': True|False,
        'FileTransferUploadStreams': 123,
        'LoadTimeout': 123,
        'MaxFileSize': 123,
        'Password': 'string',
        'Port': 123,
        'RemoveQuotes': True|False,
        'ReplaceInvalidChars': 'string',
        'ReplaceChars': 'string',
        'ServerName': 'string',
        'ServiceAccessRoleArn': 'string',
        'ServerSideEncryptionKmsKeyId': 'string',
        'TimeFormat': 'string',
        'TrimBlanks': True|False,
        'TruncateColumns': True|False,
        'Username': 'string',
        'WriteBufferSize': 123,
        'SecretsManagerAccessRoleArn': 'string',
        'SecretsManagerSecretId': 'string'
    },
    PostgreSQLSettings={
        'AfterConnectScript': 'string',
        'CaptureDdls': True|False,
        'MaxFileSize': 123,
        'DatabaseName': 'string',
        'DdlArtifactsSchema': 'string',
        'ExecuteTimeout': 123,
        'FailTasksOnLobTruncation': True|False,
        'HeartbeatEnable': True|False,
        'HeartbeatSchema': 'string',
        'HeartbeatFrequency': 123,
        'Password': 'string',
        'Port': 123,
        'ServerName': 'string',
        'Username': 'string',
        'SlotName': 'string',
        'PluginName': 'no-preference'|'test-decoding'|'pglogical',
        'SecretsManagerAccessRoleArn': 'string',
        'SecretsManagerSecretId': 'string'
    },
    MySQLSettings={
        'AfterConnectScript': 'string',
        'CleanSourceMetadataOnMismatch': True|False,
        'DatabaseName': 'string',
        'EventsPollInterval': 123,
        'TargetDbType': 'specific-database'|'multiple-databases',
        'MaxFileSize': 123,
        'ParallelLoadThreads': 123,
        'Password': 'string',
        'Port': 123,
        'ServerName': 'string',
        'ServerTimezone': 'string',
        'Username': 'string',
        'SecretsManagerAccessRoleArn': 'string',
        'SecretsManagerSecretId': 'string'
    },
    OracleSettings={
        'AddSupplementalLogging': True|False,
        'ArchivedLogDestId': 123,
        'AdditionalArchivedLogDestId': 123,
        'AllowSelectNestedTables': True|False,
        'ParallelAsmReadThreads': 123,
        'ReadAheadBlocks': 123,
        'AccessAlternateDirectly': True|False,
        'UseAlternateFolderForOnline': True|False,
        'OraclePathPrefix': 'string',
        'UsePathPrefix': 'string',
        'ReplacePathPrefix': True|False,
        'EnableHomogenousTablespace': True|False,
        'DirectPathNoLog': True|False,
        'ArchivedLogsOnly': True|False,
        'AsmPassword': 'string',
        'AsmServer': 'string',
        'AsmUser': 'string',
        'CharLengthSemantics': 'default'|'char'|'byte',
        'DatabaseName': 'string',
        'DirectPathParallelLoad': True|False,
        'FailTasksOnLobTruncation': True|False,
        'NumberDatatypeScale': 123,
        'Password': 'string',
        'Port': 123,
        'ReadTableSpaceName': True|False,
        'RetryInterval': 123,
        'SecurityDbEncryption': 'string',
        'SecurityDbEncryptionName': 'string',
        'ServerName': 'string',
        'SpatialDataOptionToGeoJsonFunctionName': 'string',
        'StandbyDelayTime': 123,
        'Username': 'string',
        'UseBFile': True|False,
        'UseDirectPathFullLoad': True|False,
        'UseLogminerReader': True|False,
        'SecretsManagerAccessRoleArn': 'string',
        'SecretsManagerSecretId': 'string',
        'SecretsManagerOracleAsmAccessRoleArn': 'string',
        'SecretsManagerOracleAsmSecretId': 'string'
    },
    SybaseSettings={
        'DatabaseName': 'string',
        'Password': 'string',
        'Port': 123,
        'ServerName': 'string',
        'Username': 'string',
        'SecretsManagerAccessRoleArn': 'string',
        'SecretsManagerSecretId': 'string'
    },
    MicrosoftSQLServerSettings={
        'Port': 123,
        'BcpPacketSize': 123,
        'DatabaseName': 'string',
        'ControlTablesFileGroup': 'string',
        'Password': 'string',
        'QuerySingleAlwaysOnNode': True|False,
        'ReadBackupOnly': True|False,
        'SafeguardPolicy': 'rely-on-sql-server-replication-agent'|'exclusive-automatic-truncation'|'shared-automatic-truncation',
        'ServerName': 'string',
        'Username': 'string',
        'UseBcpFullLoad': True|False,
        'UseThirdPartyBackupDevice': True|False,
        'SecretsManagerAccessRoleArn': 'string',
        'SecretsManagerSecretId': 'string'
    },
    IBMDb2Settings={
        'DatabaseName': 'string',
        'Password': 'string',
        'Port': 123,
        'ServerName': 'string',
        'SetDataCaptureChanges': True|False,
        'CurrentLsn': 'string',
        'MaxKBytesPerRead': 123,
        'Username': 'string',
        'SecretsManagerAccessRoleArn': 'string',
        'SecretsManagerSecretId': 'string'
    },
    ResourceIdentifier='string',
    DocDbSettings={
        'Username': 'string',
        'Password': 'string',
        'ServerName': 'string',
        'Port': 123,
        'DatabaseName': 'string',
        'NestingLevel': 'none'|'one',
        'ExtractDocId': True|False,
        'DocsToInvestigate': 123,
        'KmsKeyId': 'string',
        'SecretsManagerAccessRoleArn': 'string',
        'SecretsManagerSecretId': 'string'
    }
)
```
- EndpointIdentifier: The database endpoint identifier. Identifiers must begin with a letter and must contain only ASCII letters, digits, and hyphens
- EndpointType: The type of endpoint. Valid values are source and target .
- EngineName: The type of engine for the endpoint. Valid values, depending on the EndpointType value, include "mysql" , "oracle" , "postgres" , "mariadb" , "aurora" , "aurora-postgresql" , "redshift" , "s3" , "db2" , "azuredb" , "sybase" , "dynamodb" , "mongodb" , "kinesis" , "kafka" , "elasticsearch" , "docdb" , "sqlserver" , and "neptune" .
- DynamoDB Settings: [https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Target.DynamoDB.html#CHAP_Target.DynamoDB.ObjectMapping]
- S3Settings: [https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Target.S3.html#CHAP_Target.S3.Configuring]
    - ServiceAccessRoleArn: he Amazon Resource Name (ARN) used by the service to access the IAM role.
    - ExternalTableDefinition: Specifies how tables are defined in the S3 source files only.
    - CsvRowDelimiter: The delimiter used to separate rows in the .csv file for both source and target. The default is a carriage return (\n ).
    - CsvDelimiter: The delimiter used to separate columns in the .csv file for both source and target. The default is a comma.
    - BucketFolder:An optional parameter to set a folder name in the S3 bucket. If provided, tables are created in the path `` bucketFolder /schema_name /table_name /`` . If this parameter isn't specified, then the path used is `` schema_name /table_name /`` .
    - BucketName: The name of the S3 bucket.
    - CompressionType: An optional parameter to use GZIP to compress the target files. 
    - EncryptionMode: You can choose either SSE_S3 (the default) or SSE_KMS .
    - To use SSE_S3 , you need an Identity and Access Management (IAM) role with permission to allow "arn:aws:s3:::dms-*" to use the following actions:
- MongoDbSettings:
    - same as mysql Connection
- KinesisSettings:
    - StreamArn: The Amazon Resource Name (ARN) for the Amazon Kinesis Data Streams endpoint.
    - MessageFormat: The output format for the records created on the endpoint. The message format is JSON (default) or JSON_UNFORMATTED (a single line with no tab).
    - ServiceAccessRoleArn: The Amazon Resource Name (ARN) for the IAM role that DMS uses to write to the Kinesis data stream. The role must allow the iam:PassRole action.
    - IncludeTransactionDetails: Provides detailed transaction information from the source database
    - IncludePartitionValue: Shows the partition value within the Kinesis message output, unless the partition type is schema-table-type . The default is false .
- KafkaSettings:
    - Settings in JSON format for the target Apache Kafka endpoint. For more information about the available settings, see [https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Target.Kafka.html#CHAP_Target.Kafka.ObjectMapping] in the Database Migration Service User Guide.
    - Broker:A comma-separated list of one or more broker locations in your Kafka cluster that host your Kafka instance. Specify each broker location in the form `` broker-hostname-or-ip :port `` . For example, "ec2-12-345-678-901.compute-1.amazonaws.com:2345"
    - Topic: The topic to which you migrate the data. If you don't specify a topic, DMS specifies "kafka-default-topic" as the migration topic.
    - MessageFormat: The output format for the records created on the endpoint. The message format is JSON (default) or JSON_UNFORMATTED (a single line with no tab).
- ElasticsearchSettings: 
    - Settings in JSON format for the target Elasticsearch endpoint. For more information about the available settings, see Extra Connection Attributes When Using Elasticsearch as a Target for DMS in the Database Migration Service User Guide .
- PostgreSQLSettings:
    - same as mysql setting
- MySQLSettings:
    - same

#### create_event_subscription
reates an DMS event notification subscription.

You can specify the type of source (SourceType ) you want to be notified of, provide a list of DMS source IDs (SourceIds ) that triggers the events, and provide a list of event categories (EventCategories ) for events you want to be notified of. If you specify both the SourceType and SourceIds , such as SourceType = replication-instance and SourceIdentifier = my-replinstance , you will be notified of all the replication instance events for the specified source. If you specify a SourceType but don't specify a SourceIdentifier , you receive notice of the events for that source type for all your DMS sources. If you don't specify either SourceType nor SourceIdentifier , you will be notified of events generated from all DMS sources belonging to your customer account.
```python
response = client.create_event_subscription(
    SubscriptionName='string',
    SnsTopicArn='string',
    SourceType='string',
    EventCategories=[
        'string',
    ],
    SourceIds=[
        'string',
    ],
    Enabled=True|False,
    Tags=[
        {
            'Key': 'string',
            'Value': 'string'
        },
    ]
)
```
- SubscriptionName: The name of the DMS event notification subscription. This name must be less than 255 characters.
- SnsTopicArn: The Amazon Resource Name (ARN) of the Amazon SNS topic created for event notification. The ARN is created by Amazon SNS when you create a topic and subscribe to it.
- SourceType: The type of DMS resource that generates the events. Valid values: replication-instance | replication-task
- EventCategories: A list of event categories for a source type that you want to subscribe to
- SourceIds: A list of identifiers for which DMS provides notification events.
- Enabled: A Boolean value; set to true to activate the subscription, or set to false to create the subscription but not activate it.
- Exception:
    - DatabaseMigrationService.Client.exceptions.ResourceQuotaExceededFault
    - DatabaseMigrationService.Client.exceptions.ResourceNotFoundFault
    - DatabaseMigrationService.Client.exceptions.ResourceAlreadyExistsFault
    - DatabaseMigrationService.Client.exceptions.SNSInvalidTopicFault
    - DatabaseMigrationService.Client.exceptions.SNSNoAuthorizationFault


#### create_replication_instance
DMS requires that your account have certain roles with appropriate permissions before you can create a replication instance. For information on the required roles, see Creating the IAM Roles to Use With the CLI and DMS API . For information on the required permissions, see IAM Permissions Needed to Use DMS .
```python
response = client.create_replication_instance(
    ReplicationInstanceIdentifier='string',
    AllocatedStorage=123,
    ReplicationInstanceClass='string',
    VpcSecurityGroupIds=[
        'string',
    ],
    AvailabilityZone='string',
    ReplicationSubnetGroupIdentifier='string',
    PreferredMaintenanceWindow='string',
    MultiAZ=True|False,
    EngineVersion='string',
    AutoMinorVersionUpgrade=True|False,
    Tags=[
        {
            'Key': 'string',
            'Value': 'string'
        },
    ],
    KmsKeyId='string',
    PubliclyAccessible=True|False,
    DnsNameServers='string',
    ResourceIdentifier='string'
)
```
- ReplicationInstanceIdentifier: Must contain 1-63 alphanumeric characters or hyphens.
- AllocatedStorage: he amount of storage (in gigabytes) to be initially allocated for the replication instance.
- ReplicationInstanceClass: The compute and memory capacity of the replication instance as defined for the specified replication instance class. For example to specify the instance class dms.c4.large, set this parameter to "dms.c4.large" .
- VpcSecurityGroupIds: Specifies the VPC security group to be used with the replication instance.
- AvailabilityZone: example: us-east-1d
- MultiAZ: true
- EngineVersion: If an engine version number is not specified when a replication instance is created, the default is the latest engine version available.
- AutoMinorVersionUpgrade: Default: true
- Exceptions:
    - DatabaseMigrationService.Client.exceptions.AccessDeniedFault
    - DatabaseMigrationService.Client.exceptions.ResourceAlreadyExistsFault
    - DatabaseMigrationService.Client.exceptions.InsufficientResourceCapacityFault
    - DatabaseMigrationService.Client.exceptions.ResourceQuotaExceededFault
    - DatabaseMigrationService.Client.exceptions.StorageQuotaExceededFault
    - DatabaseMigrationService.Client.exceptions.ResourceNotFoundFault
    - DatabaseMigrationService.Client.exceptions.ReplicationSubnetGroupDoesNotCoverEnoughAZs
    - DatabaseMigrationService.Client.exceptions.InvalidResourceStateFault
    - DatabaseMigrationService.Client.exceptions.InvalidSubnet
    - DatabaseMigrationService.Client.exceptions.KMSKeyNotAccessibleFault
 
 #### create_replication_task
 Creates a replication task using the specified parameters.
 ```python
 response = client.create_replication_task(
    ReplicationTaskIdentifier='string',
    SourceEndpointArn='string',
    TargetEndpointArn='string',
    ReplicationInstanceArn='string',
    MigrationType='full-load'|'cdc'|'full-load-and-cdc',
    TableMappings='string',
    ReplicationTaskSettings='string',
    CdcStartTime=datetime(2015, 1, 1),
    CdcStartPosition='string',
    CdcStopPosition='string',
    Tags=[
        {
            'Key': 'string',
            'Value': 'string'
        },
    ],
    TaskData='string',
    ResourceIdentifier='string'
)
```
- ReplicationTaskIdentifier: Must contain 1-255 alphanumeric characters or hyphens.
- SourceEndpointArn: An Amazon Resource Name (ARN) that uniquely identifies the source endpoint.
- TargetEndpointArn: An Amazon Resource Name (ARN) that uniquely identifies the target endpoint.
- ReplicationInstanceArn: The Amazon Resource Name (ARN) of a replication instance.
- MigrationType: The migration type. Valid values: full-load | cdc | full-load-and-cdc
- TableMappings: The table mappings for the task, in JSON format. For more information, [see Using Table Mapping to Specify Task Settings](https://docs.aws.amazon.com/dms/latest/userguide/CHAP_Tasks.CustomizingTasks.TableMapping.html) in the Database Migration Service User Guide.
- ReplicationTaskSettings:  Overall settings for the task, in JSON format.
- CdcStartTime: Indicates the start time for a change data capture (CDC) operation. Use either CdcStartTime or CdcStartPosition to specify when you want a CDC operation to start. Specifying both values results in an error.
- Exceptions:
    - DatabaseMigrationService.Client.exceptions.AccessDeniedFault
    - DatabaseMigrationService.Client.exceptions.InvalidResourceStateFault
    - DatabaseMigrationService.Client.exceptions.ResourceAlreadyExistsFault
    - DatabaseMigrationService.Client.exceptions.ResourceNotFoundFault
    - DatabaseMigrationService.Client.exceptions.KMSKeyNotAccessibleFault
    - DatabaseMigrationService.Client.exceptions.ResourceQuotaExceededFault
- Example:
```python
response = client.create_replication_task(
    CdcStartTime=datetime(2016, 12, 14, 18, 25, 43, 2, 349, 0),
    MigrationType='full-load',
    ReplicationInstanceArn='arn:aws:dms:us-east-1:123456789012:rep:6UTDJGBOUS3VI3SUWA66XFJCJQ',
    ReplicationTaskIdentifier='task1',
    ReplicationTaskSettings='',
    SourceEndpointArn='arn:aws:dms:us-east-1:123456789012:endpoint:ZW5UAN6P4E77EC7YWHK4RZZ3BE',
    TableMappings='file://mappingfile.json',
    Tags=[
        {
            'Key': 'Acount',
            'Value': '24352226',
        },
    ],
    TargetEndpointArn='arn:aws:dms:us-east-1:123456789012:endpoint:ASXWXJZLNWNT5HTWCGV2BUJQ7E',
)

print(response)
```
#### reboot_replication_instance
Reboots a replication instance. Rebooting results in a momentary outage, until the replication instance becomes available again.
```python
response = client.reboot_replication_instance(
    ReplicationInstanceArn='string',
    ForceFailover=True|False
)
```
- ReplicationInstanceArn: The Amazon Resource Name (ARN) of the replication instance.
- ForceFailover (boolean) -- If this parameter is true , the reboot is conducted through a Multi-AZ failover. (If the instance isn't configured for Multi-AZ, then you can't specify true .)
- Exception:
        - DatabaseMigrationService.Client.exceptions.ResourceNotFoundFault
        - DatabaseMigrationService.Client.exceptions.InvalidResourceStateFault 

#### start_replication_task
tarts the replication task.

For more information about DMS tasks, see Working with Migration Tasks in the Database Migration Service User Guide.
```python
response = client.start_replication_task(
    ReplicationTaskArn='string',
    StartReplicationTaskType='start-replication'|'resume-processing'|'reload-target',
    CdcStartTime=datetime(2015, 1, 1),
    CdcStartPosition='string',
    CdcStopPosition='string'
)
```
- StartReplicationTaskType: A type of replication task.
- CdcStartTime: Indicates the start time for a change data capture (CDC) operation. Use either CdcStartTime or CdcStartPosition to specify when you want a CDC operation to start. Specifying both values results in an error. Timestamp Example: --cdc-start-time “2018-03-08T12:12:12”
- CdcStartPosition: The value can be in date, checkpoint, or LSN/SCN format. Date Example: --cdc-start-position “2018-03-08T12:12:12”


#### start_replication_task_assessment
```python
response = client.start_replication_task_assessment(
    ReplicationTaskArn='string'
)
```
#### stop_replication_task
```python
response = client.stop_replication_task(
    ReplicationTaskArn='string'
)
```

#### test_connection
```python
response = client.test_connection(
    ReplicationInstanceArn='string',
    EndpointArn='string'
)
```


#### reload_tables
Reloads the target database table with the source data.

```python
response = client.reload_tables(
    ReplicationTaskArn='string',
    TablesToReload=[
        {
            'SchemaName': 'string',
            'TableName': 'string'
        },
    ],
    ReloadOption='data-reload'|'validate-only'
)
```

- ReplicationTaskArn: The Amazon Resource Name (ARN) of the replication task.
- TablesToReload: The name and schema of the table to be reloaded.
        - SchemaName: The schema name of the table to be reloaded.
        - TableName: The table name of the table to be reloaded.
- ReloadOption: Options for reload. Specify data-reload to reload the data and re-validate it if validation is enabled. Specify validate-only to re-validate the table. This option applies only when validation is enabled for the task. Valid values: data-reload, validate-only, Default value is data-reload. 

