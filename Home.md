Welcome to the semantic-link-labs wiki!


## Code examples

[Best Practice Analyzer](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.html#sempy_labs.run_model_bpa)
```python
import sempy_labs as labs

dataset = '' # Enter the name or ID of your semantic model
workspace = None # Enter the name or ID of the workspace in which the semantic model resides

labs.run_model_bpa(dataset=dataset, workspace=workspace)
labs.run_model_bpa(dataset=dataset, workspace=workspace, extended=True)
```

[Vertipaq Analyzer](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.html#sempy_labs.vertipaq_analyzer)
```python
import sempy_labs as labs

dataset = '' # Enter the name or ID of your semantic model
workspace = None # Enter the name or ID of the workspace in which the semantic model resides

labs.vertipaq_analyzer(dataset=dataset, workspace=workspace)
```

[Connecting to the Tabular Object Model (TOM)](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.tom.html#sempy_labs.tom.connect_semantic_model)
```python
from sempy_labs.tom import connect_semantic_model

dataset = '' # Enter the name or ID of your semantic model
workspace = None # Enter the name or ID of the workspace in which the semantic model resides

with connect_semantic_model(dataset=dataset, workspace=workspace, readonly=True) as tom:
   for t in tom.model.Tables:
       for c in t.Columns:
          print(f"'{t.Name}'[{c.Name}]")
```

[Refresh a semantic model](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.html#sempy_labs.refresh_semantic_model)
```python
import sempy_labs as labs

dataset = '' # Enter the name or ID of your semantic model
workspace = None # Enter the name or ID of the workspace in which the semantic model resides

labs.refresh_semantic_model(dataset=dataset, workspace=workspace)
labs.refresh_semantic_model(dataset=dataset, workspace=workspace, tables = ['Sales', 'Geography'])
labs.refresh_semantic_model(dataset=dataset, workspace=workspace, tables = ['Geography', 'Calendar'], partitions = ["'Sales'[SalesFY2025]", "'Sales'[SalesFY2025]")
labs.refresh_semantic_model(dataset=dataset, workspace=workspace, visualize=True)
```

[Show connections](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.html#sempy_labs.list_connections)
```python
import sempy_labs as labs
labs.list_connections()
```

[Show shortcuts](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.html#sempy_labs.list_shortcuts)
```python
import sempy_labs as labs
workspace = None # Enter the name or ID of the workspace
labs.list_shortcuts(workspace=workspace)
```

[Show activity events](https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.admin.html#sempy_labs.admin.list_activity_events)
```python
from sempy_labs import admin
admin.list_activity_events(start_time="2025-02-15T07:55:00", end_time="2025-02-15T08:55:00", activity_filter="viewreport")
```

[Show tenant settings(https://semantic-link-labs.readthedocs.io/en/stable/sempy_labs.admin.html#sempy_labs.admin.list_tenant_settings)
```python
from sempy_labs import admin
admin.list_tenant_settings()
```


