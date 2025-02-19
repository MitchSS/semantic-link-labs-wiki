Here are some code examples which should help you get off to a quick start using this Python library. This library was designed to reduce the technical barrier to entry for complex tasks and give such power to any user - technical or not. As you can see, a great deal can be achieved through simply entering in a few parameters to the function of your choice. No real coding is necessary to gain value using this approach.

# Install Semantic Link Labs in your notebook
```python
%pip install semantic-link-labs
```

# Semantic Modeling
[Best Practice Analyzer](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.html#sempy_labs.run_model_bpa)
```python
import sempy_labs as labs

dataset = '' # Enter the name or ID of your semantic model
workspace = None # Enter the name or ID of the workspace in which the semantic model resides

labs.run_model_bpa(dataset=dataset, workspace=workspace)
labs.run_model_bpa(dataset=dataset, workspace=workspace, extended=True) # Setting extended=True will fetch Vertipaq Analyzer statistics and use them to run advanced BPA rules against your model
```

[Vertipaq Analyzer](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.html#sempy_labs.vertipaq_analyzer)
```python
import sempy_labs as labs

dataset = '' # Enter the name or ID of your semantic model
workspace = None # Enter the name or ID of the workspace in which the semantic model resides

labs.vertipaq_analyzer(dataset=dataset, workspace=workspace)
```

[Refresh a semantic model](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.html#sempy_labs.refresh_semantic_model)
```python
import sempy_labs as labs

dataset = '' # Enter the name or ID of your semantic model
workspace = None # Enter the name or ID of the workspace in which the semantic model resides

labs.refresh_semantic_model(dataset=dataset, workspace=workspace) # Refresh the entire semantic model
labs.refresh_semantic_model(dataset=dataset, workspace=workspace, tables = ['Sales', 'Geography']) # Refresh just specific tables
labs.refresh_semantic_model(dataset=dataset, workspace=workspace, tables = ['Geography', 'Calendar'], partitions = ["'Sales'[SalesFY2025]", "'Sales'[SalesFY2025]") # Refresh specific tables and specific partitions
labs.refresh_semantic_model(dataset=dataset, workspace=workspace, visualize=True) # See a visual representation of your refresh in real time.
```

## Tabular Object Model (TOM)

[Connecting to the Tabular Object Model (TOM)](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.tom.html#sempy_labs.tom.connect_semantic_model)
```python
from sempy_labs.tom import connect_semantic_model

dataset = '' # Enter the name or ID of your semantic model
workspace = None # Enter the name or ID of the workspace in which the semantic model resides

with connect_semantic_model(dataset=dataset, workspace=workspace, readonly=True) as tom:
    for t in tom.model.Tables:
        for c in t.Columns:
            print(f"'{t.Name}'[{c.Name}]") # Print the names of all tables/columns in the model
```

Set and read Vertipaq annotations
```python
from sempy_labs.tom import connect_semantic_model

dataset = '' # Enter the name or ID of your semantic model
workspace = None # Enter the name or ID of the workspace in which the semantic model resides

with connect_semantic_model(dataset=dataset, workspace=workspace, readonly=False) as tom:
    tom.set_vertipaq_annotations()

with connect_semantic_model(dataset=dataset, workspace=workspace, readonly=True) as tom:
    for t in tom.model.Tables:
        print(f"{t.Name} : {tom.total_size(object=t)}") # Shows the total size (in bytes) of each table in your semantic model

```

## Direct Lake
[Update the connection of a Direct Lake semantic model](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.directlake.html#sempy_labs.directlake.update_direct_lake_model_connection)
```python
from sempy_labs import directlake

dataset = '' # Enter the name or ID of your semantic model
workspace = None # Enter the name or ID of the workspace in which the semantic model resides
source = 'MyLakehouse' # The name or ID of the lakehouse/warehouse
source_type = "Lakehouse" # Can either be 'Lakehouse' or 'Warehouse'
source_workspace = 'MyLakehouseWorkspace' # Enter the name or ID of the workspace in which the lakehouse/warehouse exists

directlake.update_direct_lake_model_connection(dataset=dataset, workspace=workspace, source=source, source_type=source_type, source_workspace=source_workspace)
```

# Admin
[Show activity events](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.admin.html#sempy_labs.admin.list_activity_events)
```python
from sempy_labs import admin

start_time = "2025-02-15T07:55:00"
end_time = "2025-02-15T08:55:00"
activity_filter = "viewreport"
admin.list_activity_events(start_time=start_time, end_time=end_time, activity_filter=activity_filter)
```

[Show tenant settings](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.admin.html#sempy_labs.admin.list_tenant_settings)
```python
from sempy_labs import admin

admin.list_tenant_settings()
```

[Show connections](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.html#sempy_labs.list_connections)
```python
import sempy_labs as labs

labs.list_connections()
```

# Lakehouses
[Show tables within a lakehouse](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.lakehouse.html#sempy_labs.lakehouse.get_lakehouse_tables)
```python
import sempy_labs.lakehouse as lake

lakehouse = None # Enter the name or ID of the lakehouse
workspace = None # Enter the name or ID of the workspace in which the lakehouse exists

lake.get_lakehouse_tables(lakehouse=lakehouse, workspace=workspace)
```

[Show columns within all tables within a lakehouse](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.lakehouse.html#sempy_labs.lakehouse.get_lakehouse_columns)
```python
import sempy_labs.lakehouse as lake

lakehouse = None # Enter the name or ID of the lakehouse
workspace = None # Enter the name or ID of the workspace in which the lakehouse exists

lake.get_lakehouse_columns(lakehouse=lakehouse, workspace=workspace)
```

[Show shortcuts](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.html#sempy_labs.list_shortcuts)
```python
import sempy_labs as labs

workspace = None # Enter the name or ID of the workspace

labs.list_shortcuts(workspace=workspace)
```

[Create a OneLake shortcut](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.lakehouse.html#sempy_labs.lakehouse.create_shortcut_onelake)
```python
import sempy_labs.lakehouse as lake

table_name = 'MyTable' # Enter the name of the table on which the shortcut will be based
source_lakehouse = 'MyLakehouse1' # Enter the name of the lakehouse in which the table exists
source_workspace = 'MyLakehouse1Workspace' # Enter the name of the workspace in which the source lakehouse exists
destination_lakehouse = 'MyLakehouse2' # Enter the name of the lakehouse in which the shortcut will be created
destination_workspace = 'MyLakehouse2Workspace' # Enter the name of the workspace in which the destination lakehouse exists
shortcut_name = None # Enter the name of the shortcut which will be created. By default it is named after the table_name

lake.create_shortcut_onelake(table_name=table_name, source_lakehouse=source_lakehouse, source_workspace=source_workspace, destination_lakehouse=destination_lakehouse, destination_workspace=destination_workspace, shortcut_name=shortcut_name)
```


# Reports
[Rebind a report to a different semantic model](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.report.html#sempy_labs.report.report_rebind)
```python
import sempy_labs.report as rep

report = '' # Name or ID of the report
dataset = '' # Name or ID of the semantic model to bind to the report
report_workspace = None # Name or ID of the workspace in which the report resides
dataset_workspace = None # Name or ID of the workspace in which the semantic model resides

rep.rebind_report(report=report, dataset=dataset, report_workspace=report_workspace, dataset_workspace=dataset_workspace)
```

