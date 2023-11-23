### HBase Commands with Explanations and Examples:

### 1. **Table Management Commands:**

#### a. **Create a Table:**
```shell
create '<table_name>', '<column_family1>', '<column_family2>', ...
```
- Example:
  ```shell
  create 'employee', 'personal_info', 'professional_info'
  ```

#### b. **List Tables:**
```shell
list
```
- Example:
  ```shell
  list
  ```

#### c. **Describe a Table:**
```shell
describe '<table_name>'
```
- Example:
  ```shell
  describe 'employee'
  ```

#### d. **Disable and Enable a Table:**
```shell
disable '<table_name>'
enable '<table_name>'
```
- Example:
  ```shell
  disable 'employee'
  enable 'employee'
  ```

#### e. **Delete a Table:**
```shell
drop '<table_name>'
```
- Example:
  ```shell
  drop 'employee'
  ```

### 2. **Data Manipulation Commands:**

#### a. **Insert Data:**
```shell
put '<table_name>', '<row_key>', '<column_family:column_qualifier>', '<value>'
```
- Example:
  ```shell
  put 'employee', '1001', 'personal_info:name', 'John Doe'
  ```

#### b. **Get Data:**
```shell
get '<table_name>', '<row_key>'
```
- Example:
  ```shell
  get 'employee', '1001'
  ```

#### c. **Scan Table:**
```shell
scan '<table_name>'
```
- Example:
  ```shell
  scan 'employee'
  ```

#### d. **Delete Data:**
```shell
delete '<table_name>', '<row_key>', '<column_family:column_qualifier>'
```
- Example:
  ```shell
  delete 'employee', '1001', 'personal_info:name'
  ```

#### e. **Delete a Row:**
```shell
deleteall '<table_name>', '<row_key>'
```
- Example:
  ```shell
  deleteall 'employee', '1001'
  ```

### 3. **Advanced Commands:**

#### a. **Count Rows in a Table:**
```shell
count '<table_name>'
```
- Example:
  ```shell
  count 'employee'
  ```

#### b. **Major Compact a Table:**
```shell
major_compact '<table_name>'
```
- Example:
  ```shell
  major_compact 'employee'
  ```

#### c. **Flush a Table:**
```shell
flush '<table_name>'
```
- Example:
  ```shell
  flush 'employee'
  ```

#### d. **Run a Shell Script:**
```shell
hbase shell '<script_path>'
```
- Example:
  ```shell
  hbase shell '/path/to/script.hbase'
  ```

### Conclusion:

HBase commands provide a powerful interface for managing tables, inserting and retrieving data, and performing various administrative tasks. Understanding and using these commands is essential for efficiently working with HBase in a distributed environment.
