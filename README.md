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
