Here’s a table listing important **Apache Ozone commands** with the specified format:

| **Type of Command** | **What the Command Does**                                  | **Command**                              |
|----------------------|-----------------------------------------------------------|------------------------------------------|
| **Volume**          | Creates a new volume.                                      | `ozone sh volume create /volume_name`    |
| **Volume**          | Lists all accessible volumes.                              | `ozone sh volume list`                   |
| **Volume**          | Retrieves details of a specific volume.                    | `ozone sh volume info /volume_name`      |
| **Volume**          | Deletes a volume.                                          | `ozone sh volume delete /volume_name`    |
| **Volume**          | Gets the Access Control List (ACL) of a volume.            | `ozone sh volume getacl /volume_name`    |
| **Bucket**          | Creates a new bucket in a specific volume.                 | `ozone sh bucket create /volume_name/bucket_name` |
| **Bucket**          | Lists all buckets in a specific volume.                    | `ozone sh bucket list /volume_name`      |
| **Bucket**          | Retrieves details of a specific bucket.                    | `ozone sh bucket info /volume_name/bucket_name` |
| **Bucket**          | Deletes a bucket from a volume.                            | `ozone sh bucket delete /volume_name/bucket_name` |
| **Key**             | Uploads a file as a key in a bucket.                       | `ozone sh key put /volume_name/bucket_name/key_name /local_file_path` |
| **Key**             | Downloads a key (file) from a bucket.                      | `ozone sh key get /volume_name/bucket_name/key_name /local_file_path` |
| **Key**             | Lists all keys in a specific bucket.                       | `ozone sh key list /volume_name/bucket_name` |
| **Key**             | Deletes a key from a bucket.                               | `ozone sh key delete /volume_name/bucket_name/key_name` |
| **Admin**           | Shows the cluster summary.                                 | `ozone admin cluster-summary`            |
| **Admin**           | Checks the status of Safe Mode in the cluster.             | `ozone admin safemode status`            |
| **Admin**           | Exits Safe Mode in the cluster.                            | `ozone admin safemode leave`             |
| **Admin**           | Starts the Ozone Manager (OM) service.                     | `ozone daemon start om`                  |
| **Admin**           | Starts the DataNode (DN) service.                          | `ozone daemon start datanode`            |
| **Filesystem**      | Lists files and directories in the Ozone filesystem.       | `ozone fs -ls [path]`                    |
| **Filesystem**      | Uploads a local file to the Ozone filesystem.              | `ozone fs -put /local_file_path [ozone_path]` |
| **Filesystem**      | Downloads a file from the Ozone filesystem to local.       | `ozone fs -get [ozone_path] /local_file_path` |
| **Filesystem**      | Deletes a file or directory in the Ozone filesystem.       | `ozone fs -rm [path]`                    |

Let me know if you want to add more commands or refine the table!


Here are additional **important commands** in Apache Ozone to manage and retrieve information about the **Ozone Manager (OM)**, **Storage Container Manager (SCM)**, and the overall cluster:

---

| **Type of Command** | **What the Command Does**                                      | **Command**                              |
|----------------------|---------------------------------------------------------------|------------------------------------------|
| **OM**              | Retrieves details of the Ozone Manager (OM) service.          | `ozone admin om getserviceroles`         |
| **OM**              | Lists all Ozone Manager nodes in the cluster.                 | `ozone admin om list`                    |
| **SCM**             | Retrieves the status of the Storage Container Manager (SCM).  | `ozone admin scm status`                 |
| **SCM**             | Lists all SCM nodes in the cluster.                           | `ozone admin scm list`                   |
| **SCM**             | Retrieves the service roles of SCM (leader, follower, etc.).  | `ozone admin scm getserviceroles`        |
| **Cluster**         | Displays the overall health and status of the cluster.        | `ozone admin cluster-summary`            |
| **Cluster**         | Lists all nodes in the cluster (OM, SCM, Datanodes).          | `ozone admin node list`                  |
| **Cluster**         | Displays information about pipelines (used for containers).   | `ozone admin pipeline list`              |
| **Safe Mode**       | Checks the current Safe Mode status of the cluster.           | `ozone admin safemode status`            |
| **Safe Mode**       | Exits the cluster from Safe Mode.                             | `ozone admin safemode leave`             |
| **Datanode**        | Lists all registered Datanodes in the cluster.                | `ozone admin datanode list`              |
| **Datanode**        | Displays detailed info about a specific Datanode.             | `ozone admin datanode info [node_id]`    |
| **Ratis (Replication)** | Displays Ratis group info for replication.                  | `ozone admin ratis list`                 |
| **Logs**            | Retrieves logs for debugging the Ozone services.              | `ozone admin logs get [log_file_name]`   |
| **Configuration**   | Displays all configuration settings of Ozone.                 | `ozone admin config list`                |
| **Quota**           | Displays quota usage of a volume or bucket.                   | `ozone admin quota get [volume/bucket]`  |
| **Audit**           | Displays audit logs for tracking user operations.             | `ozone admin audit log`                  |

---

### **Other Helpful Commands**
#### **General Troubleshooting**
- **Verify Ozone Services**:
  ```bash
  ozone admin om status
  ozone admin scm status
  ```
- **Restart a Service**:
  ```bash
  ozone daemon restart om
  ozone daemon restart scm
  ```
- **Stop a Service**:
  ```bash
  ozone daemon stop om
  ozone daemon stop scm
  ```

#### **Key Management Commands**
- **Rename a Key**:
  ```bash
  ozone sh key rename /volume_name/bucket_name/key_name /new_key_name
  ```

#### **Cluster Administration**
- **Force a Leader Election** (for OM or SCM):
  ```bash
  ozone admin om re-election
  ozone admin scm re-election
  ```

- **List All Containers**:
  ```bash
  ozone admin container list
  ```

---

### **Recommended Usage**
- Use **`ozone admin cluster-summary`** frequently to monitor the cluster's overall health.
- Use **`ozone admin safemode status`** during startup to ensure the cluster exits Safe Mode properly.
- Use **`ozone admin audit log`** to debug any user-related operations for compliance or troubleshooting.








Apache Ozone provides **S3-compatible APIs** for object storage, enabling you to interact with it using commands similar to those in AWS S3. Here's a detailed guide to **Ozone S3 commands** and how you can use them:

---

### **Setting Up Ozone for S3 Commands**
1. **Enable S3 Gateway**:
   - The S3 Gateway must be enabled in your Ozone setup to use S3-compatible commands.
   - You can configure it in the Ozone properties file (`ozone-site.xml`):
     ```xml
     <property>
         <name>ozone.s3g.address</name>
         <value>0.0.0.0:9878</value>
     </property>
     ```

2. **Obtain S3 Credentials**:
   - Use `ozone admin user getsecret [username]` to get the access and secret keys.
   - Example:
     ```bash
     ozone admin user getsecret myuser
     ```

3. **Configure S3 Client (Optional)**:
   - If using an S3 CLI tool like **AWS CLI** or **s3cmd**, configure your credentials with the Ozone S3 Gateway details.

---

### **Important Ozone S3 Commands**

| **Command Type**         | **What the Command Does**                               | **Command** Example                                                 |
|---------------------------|--------------------------------------------------------|----------------------------------------------------------------------|
| **Bucket Management**     | Create an S3 bucket.                                   | `aws s3api create-bucket --bucket mybucket --endpoint-url=http://localhost:9878` |
| **Bucket Management**     | List all S3 buckets.                                   | `aws s3api list-buckets --endpoint-url=http://localhost:9878`       |
| **Bucket Management**     | Delete an S3 bucket.                                   | `aws s3api delete-bucket --bucket mybucket --endpoint-url=http://localhost:9878` |
| **Object Management**     | Upload a file to an S3 bucket.                         | `aws s3 cp /path/to/local/file s3://mybucket/ --endpoint-url=http://localhost:9878` |
| **Object Management**     | Download a file from an S3 bucket.                     | `aws s3 cp s3://mybucket/file /path/to/local/ --endpoint-url=http://localhost:9878` |
| **Object Management**     | List objects in an S3 bucket.                          | `aws s3 ls s3://mybucket/ --endpoint-url=http://localhost:9878`     |
| **Object Management**     | Delete an object from an S3 bucket.                    | `aws s3 rm s3://mybucket/file --endpoint-url=http://localhost:9878` |
| **Object Management**     | Perform a recursive upload of a directory.             | `aws s3 cp /local/dir s3://mybucket/ --recursive --endpoint-url=http://localhost:9878` |
| **Object Management**     | Perform a recursive download of a directory.           | `aws s3 cp s3://mybucket/ /local/dir --recursive --endpoint-url=http://localhost:9878` |
| **Object Management**     | List objects recursively in an S3 bucket.              | `aws s3 ls s3://mybucket/ --recursive --endpoint-url=http://localhost:9878` |
| **Permissions**           | Add permissions to a bucket (ACL).                     | `aws s3api put-bucket-acl --bucket mybucket --acl public-read --endpoint-url=http://localhost:9878` |
| **Permissions**           | Get permissions (ACL) of a bucket.                     | `aws s3api get-bucket-acl --bucket mybucket --endpoint-url=http://localhost:9878` |
| **Policy Management**     | Add a bucket policy to allow public access.            | `aws s3api put-bucket-policy --bucket mybucket --policy file://policy.json --endpoint-url=http://localhost:9878` |
| **Policy Management**     | Get the bucket policy.                                 | `aws s3api get-bucket-policy --bucket mybucket --endpoint-url=http://localhost:9878` |
| **Multipart Upload**      | Perform multipart upload for large files.              | `aws s3 cp largefile s3://mybucket/ --endpoint-url=http://localhost:9878` |
| **Lifecycle Management**  | Configure lifecycle rules for a bucket.                | `aws s3api put-bucket-lifecycle-configuration --bucket mybucket --lifecycle-configuration file://lifecycle.json --endpoint-url=http://localhost:9878` |

---

### **Using S3 CLI Tools with Ozone**
You can use tools like **AWS CLI**, **s3cmd**, or libraries like **boto3** to interact with Ozone’s S3 interface.

#### Example: Configuring AWS CLI for Ozone
1. **Set Up a Profile**:
   ```bash
   aws configure --profile ozone
   ```
   Enter the following details:
   - Access Key: From `ozone admin user getsecret`.
   - Secret Key: From `ozone admin user getsecret`.
   - Region: `us-east-1` (or any dummy value).
   - Endpoint URL: The S3 Gateway URL (e.g., `http://localhost:9878`).

2. **Run S3 Commands**:
   ```bash
   aws s3 ls --profile ozone --endpoint-url http://localhost:9878
   ```

---

### **Advanced Use Cases**
- **Data Backup**: Use `aws s3 sync` to synchronize local directories with an Ozone S3 bucket.
  ```bash
  aws s3 sync /local/path s3://mybucket/ --endpoint-url=http://localhost:9878
  ```

- **Scripting**: Automate object storage workflows with AWS CLI or Python’s boto3 library.

- **Testing with MinIO Client**: If using the MinIO client (`mc`), you can add an alias for Ozone:
  ```bash
  mc alias set ozone http://localhost:9878 <access_key> <secret_key>
  ```

---

Let me know if you need help setting up or troubleshooting specific S3 commands in Ozone!
