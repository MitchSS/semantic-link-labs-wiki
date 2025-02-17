Here are some tips & tricks when working with Semantic Link Labs!

### Scripts
* Check out the following [GitHub repo](https://github.com/m-kovalsky/Fabric) for useful scripts for Semantic Link & Semantic Link Labs

### Importing
* When importing the library and packages, make sure to follow [this standard](https://github.com/microsoft/semantic-link-labs?tab=readme-ov-file#once-installed-run-this-code-to-import-the-library-into-your-notebook) as it is aligned with the documentation and keeps things simple. The reason for following the recommendation below is that functions may be reorganized to different files. In that case, if you were using the first snippet (shown below) your code would break. The second code snippet (shown below) would not be impacted and is therefore more robust.

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
* Semantic Link Labs may be used in either a PySpark or Python notebook in Microsoft Fabric. Generally speaking, most functions can be executed using a Python notebook. Using a Python notebook will generally start up faster and be a better experience (and cheaper). Some functions (and using some parameters within some functions) necessitate Spark which necessitate a PySpark notebook. For example, run_model_bpa can be executed in a Python notebook. However, if you set the 'export' parameter to True, it uses Spark. Hence, in that case you need to run the function in a PySpark notebook. Work is being done to increase the percentage of functionality of Semantic Link Labs which can be run in a Python notebook (while keeping all existing functionality). As of version 0.9.3, a friendly error message will show if you attempt to use a function which requires a PySpark notebook in a Python notebook.