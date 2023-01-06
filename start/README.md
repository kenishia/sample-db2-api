<!---
 Copyright IBM Corp. 2021
-->
# EmployeesApi
The `start` project can be enhanced to allow users to create, read, update, and delete employees in the Db2 sample employee table (DSN8B10.EMP).

## Configuration
To be able to connect to the Db2 instance in which you have the target db2 service/stored procedure installed, a file named `db2.xml` has been placed in the directory `./src/main/liberty/config`. 
You will need to edit the devfile.yaml to add your credentials for accessing the database.  Replace "tsoidhere" with your tso id and "passwordhere" with your password
```
      - name: DB2_USERNAME
        value: "tsoidhere"
      - name: DB2_PASSWORD
        value: "{aes}AHI+IHxZd166YhTjal48dUV9d8YISXQNj7dIcQhyS93e"
```

The variables (e.g. `${DB2_USERNAME}`) values must be provided as environment variables when the designer image is started. The provided environment variable values will then be substituted in when the connection is used.

Optionally, you can edit the devfile.yaml to reflect the name of the api you are creating.  Replace "sample-db2-api" and "stub-db2-api" with the desired name(s).
(Lines 3, 5 and 23)
```
metadata:
  name: sample-db2-api
projects:
  - name: stub-db2-api
  .
  .
  .
 env:
   - name: ZCON_DESIGNER_PROJECT
     value: /projects/stub-db2-api/start
```
## Development
You will need to create z/OS assets for the Db2 native REST services you want to use. These z/OS assets will then need to mapped into your API. You will then need to define the responses and map each response case. The `Test` button can be used to test your API incrementally as you develop it. 

See the `Create your first z/OS Connect API` topic in the IBM documentation for more details on using the IBM z/OS Connect Designer.

## Contents
The operations and paths that can be created in the API are as follows:
- GET | PUT | DELETE : /employees/{id}
- GET | POST : /employees

Review `start/src/main/api/openapi.yaml` for the full API description.
