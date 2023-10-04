### [Docs Testing]Test all available commands from "Create Project using Python" #7516

**Task 1-> Create Project:**
<br/>
case A: Use the get_project() method to get the default mindsdb project:

**(Note Some of the images may not be rendered properly, please check the asset folder to get the images and they are hinted for each image tag 
by clicking [here](https://github.com/truesoni/hacktoberfest2023/tree/main/mindsdb/issues_7516/assets))**
</br>

![image_before](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_1_A.png)

![image_after](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_1_A_res.png)

```
import mindsdb_sdk
server = mindsdb_sdk.connect(login='username', password='password')
server = mindsdb_sdk.connect('https://cloud.mindsdb.com', login='username', password='password')

# Use case1Alpha - Getting the available default project
project = server.get_project()
print(project)
```
**Output:**
````
project(mindsdb)
````

case B: Use the create_project() method to create a new project:

```
import mindsdb_sdk
server = mindsdb_sdk.connect(login='username', password='password')
server = mindsdb_sdk.connect('https://cloud.mindsdb.com', login='username', password='password')

# #Create case1Beta - Creating a new project and fetching it
project = server.get_project('python_sdk_project')

```
### Result:
Output before:
```
Project doesn't exist
```

Output after:
```
project('python_sdk_project')
```

</br>

![image_before](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_1_B_before.png)

![image_after_editor](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_1_B_after_editor.png)

![image_after_cloud](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_1_B_after_cloud.png)


Command: Remove a Project:<br/>
Result: Code run successfully<br/>

case A: when no project exists:
</br>

![image_before](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_1_B_before.png)

![image_after_editor](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_2_A_before.png)

![image_after_cloud](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_2_A_after.png)

Code:
```
import mindsdb_sdk

server = mindsdb_sdk.connect(login='username', password='password')
server = mindsdb_sdk.connect('https://cloud.mindsdb.com', login='username', password='password')

project = server.drop_project()
print(project)
```

Output: 
```
None
```
case B: Delete an existing Project:

<br/>

Command: DROP PROJECT test using Python<br/>
Result: Code runs successfully and Project gets deleted<br/>

**Code:**
Step 1: Create two projects project_A and project_B
```
import mindsdb_sdk

server = mindsdb_sdk.connect(login='username', password='password')
server = mindsdb_sdk.connect('https://cloud.mindsdb.com', login='username', password='password')

project_A = server.create_project('project_A')
project_B = server.create_project('project_B')

print(project_A)
print(project_B)
```

Step 2: Remove any of them 
```
import mindsdb_sdk

server = mindsdb_sdk.connect(login='username', password='password')
server = mindsdb_sdk.connect('https://cloud.mindsdb.com', login='username', password='password')

project = server.drop_project('project_1')
print(project_A)
```

</br>

![image_before](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_2_B_before_create.png)

![image_after_editor](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_2_B_after_drop.png)

![image_after_cloud](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_2_B_after_drop_cloud.png)

**Output:**
```
project(Project_B)
```
Task 3: List Project:<br/>
Syntax: Use the list_projects() method to lists all available projects:<br/>

**Code:**

```
# creating a variable for getting the list of items from the cloud server
l = server.list_projects()

print(l)
```

</br>

![image_before](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_3_before.png)

![image_after_cloud](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_3_after_cloud.png)

**Result: [project(mindsdb), project(Project_2)]**




Task 4 -> Query Projects:
<br/>

Use the query() method to submit a query to a project:

**Code:**
```
import mindsdb_sdk
server = mindsdb_sdk.connect(login='username', password='password')
server = mindsdb_sdk.connect('https://cloud.mindsdb.com', login='username', password='password')

query = server.query('SELECT * FROM example_db.house_sales')
query.fetch()
print(query)
```
Output:
````
Query(SELECT * FROM example_db.house_sales)
````

</br>

![image_before](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_4_query_cloud_before.png)

![image_after_editor](https://github.com/truesoni/hacktoberfest2023/blob/main/mindsdb/issues_7516/assets/test_4_query_editor_after.png)


### Result: All the test cases are working fine.
