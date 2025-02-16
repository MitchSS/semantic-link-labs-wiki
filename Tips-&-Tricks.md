Here are some tips & tricks when working with Semantic Link Labs!

### Importing
* When importing the library and packages, make sure to follow [this standard](https://github.com/microsoft/semantic-link-labs?tab=readme-ov-file#once-installed-run-this-code-to-import-the-library-into-your-notebook) as it is aligned with the documentation and keeps things simple. 

Do *NOT* do this:
```python
from sempy_labs._connections import list_connections
list_connections()
```
Instead do this:
```python
import sempy_labs as labs
labs.list_connections()
```

### Python vs PySpark
* Semantic Link Labs may be used in either a PySpark or Python notebook in Microsoft Fabric. Generally speaking, most functions can be executed using a Python notebook. Using a Python notebook will generally start up faster and be a better experience (and cheaper). Some functions (and using some parameters within some functions) necessitate Spark which necessitate a PySpark notebook. For example, run_model_bpa can be executed in a Python notebook. However, if you set the 'export' parameter to True, it uses Spark. Hence, in that case you need to run the function in a PySpark notebook. Work is being done to increase the percentage of functionality of Semantic Link Labs which can be run in a Python notebook (while keeping all existing functionality).