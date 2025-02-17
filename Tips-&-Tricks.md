Here are some tips & tricks when working with Semantic Link Labs!

# Scripts
* Check out the following [GitHub repo](https://github.com/m-kovalsky/Fabric) for useful scripts for Semantic Link & Semantic Link Labs

# Importing
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