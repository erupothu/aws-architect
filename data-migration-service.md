#### Database Migration Service (DMS)
Database Migration Service (DMS) can migrate your data to and from the most widely used commercial and open-source databases such as Oracle, PostgreSQL, Microsoft SQL Server, Amazon Redshift, MariaDB, Amazon Aurora, MySQL, and SAP Adaptive Server Enterprise (ASE). The service supports homogeneous migrations such as Oracle to Oracle, as well as heterogeneous migrations between different database platforms, such as Oracle to MySQL or SQL Server to PostgreSQL.

#### Python Code
```python
import boto3

client = boto3.client('dms')
```

#### These are the available methods:

* add_tags_to_resource()[add_tags_to_resource]
* apply_pending_maintenance_action()
* can_paginate()
* cancel_replication_task_assessment_run()
* create_endpoint()
* create_event_subscription()
* create_replication_instance()
* create_replication_subnet_group()
* create_replication_task()
* delete_certificate()
* delete_connection()
* delete_endpoint()
* delete_event_subscription()
* delete_replication_instance()
delete_replication_subnet_group()
delete_replication_task()
delete_replication_task_assessment_run()
describe_account_attributes()
describe_applicable_individual_assessments()
describe_certificates()
describe_connections()
describe_endpoint_settings()
describe_endpoint_types()
describe_endpoints()
describe_event_categories()
describe_event_subscriptions()
describe_events()
describe_orderable_replication_instances()
describe_pending_maintenance_actions()
describe_refresh_schemas_status()
describe_replication_instance_task_logs()
describe_replication_instances()
describe_replication_subnet_groups()
describe_replication_task_assessment_results()
describe_replication_task_assessment_runs()
describe_replication_task_individual_assessments()
describe_replication_tasks()
describe_schemas()
describe_table_statistics()
generate_presigned_url()
get_paginator()
get_waiter()
import_certificate()
list_tags_for_resource()
modify_endpoint()
modify_event_subscription()
modify_replication_instance()
modify_replication_subnet_group()
modify_replication_task()
move_replication_task()
reboot_replication_instance()
refresh_schemas()
reload_tables()
remove_tags_from_resource()
start_replication_task()
start_replication_task_assessment()
start_replication_task_assessment_run()
stop_replication_task()
test_connection()

[add_tags_to_resource]: add_tags_to_resource

welcome

