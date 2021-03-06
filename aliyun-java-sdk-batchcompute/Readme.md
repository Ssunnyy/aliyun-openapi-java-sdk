Batchcompute SDK For Java
-------------------------


### 1. 如何使用

#### (1) pom.xml 中配置


将下面xml描述放到pom.xml的dependencies标签中：

```xml
<dependency>
    <groupId>com.aliyun</groupId>
    <artifactId>aliyun-java-sdk-core</artifactId>
    <version>3.2.3</version>
</dependency>


<dependency>
    <groupId>com.aliyun</groupId>
    <artifactId>aliyun-java-sdk-batchcompute</artifactId>
    <version>4.7.0</version>
</dependency>
```

#### (2) 构造 client 对象

```java
import com.aliyuncs.batchcompute.main.v20151111.*;
...


String regionId="cn-shenzhen";
String accessKeyId="${your_access_key_id}";
String accessKeySecret="${your_access_key_secret}";

/** 构造 BatchCompute 客户端 */
BatchCompute client = new BatchComputeClient(regionId, accessKeyId, accessKeySecret);
```

#### (3) 使用 client 对象的方法:

```java
try {
    //使用客户端对象，创建Job
    CreateJobResponse response = client.createJob(job);

    //创建成功后，返回jobId
    String jobId = response.getJobId();

    System.out.println("Job created success, got jobId "+jobId);

} catch (ClientException e) {
    e.printStackTrace();

    System.out.println("Job created failed, errorCode:"+ e.getErrCode()+", errorMessage:"+e.getErrMsg());
}
```

#### (4)  client 对象支持的方法:


| 序号 | 方法 | 描述 |
| ----- | ---- | ---- |
|  | *Quota相关* | |
| 1. | getQuotas() | 查询quota |
|  | *Cluster相关* | |
| 1. | createCluster(ClusterDescription clusterDesc) | 创建Cluster |
| 2. | getCluster(String clusterId) | 获取Cluster信息 |
| 3. | deleteCluster(String clusterId) | 删除Cluster |
| 4. | listClusters(String marker, int maxItemCount) | 列举Cluster信息 |
| 5. | changeClusterDesiredVMCount(String clusterId, String groupName, int count) | 修改期望虚机数 |
|  | *ClusterInstance相关* | |
| 1. | listClusterInstances(String clusterId, String groupName) | 获取ClusterInstance 列表 |
| 2. | getClusterInstance(String clusterId, String groupName, String instanceId) | 获取ClusterInstance信息 |
| 3. | deleteClusterInstance(String clusterId,String groupName, String instanceId) | 删除ClusterInstance |
| 4. | recreateClusterInstance(String clusterId, String groupName, String instanceId) | 重新创建ClusterInstance |
|  | *Job相关* | |
| 1. | createJob(JobDescription job) | 创建Job |
| 2. | changeJobPriority(String jobId, int priority) | 设置Job优先级 |
| 3. | deleteJob(String jobId) | 删除Job |
| 4. | getJob(String jobId) | 获取Job状态信息 |
| 5. | getJobDescription(String jobId) | 获取Job描述信息 |
| 6. | stopJob(String jobId) | 停止job |
| 7. | startJob(String jobId) | 重新启动job |
| 8. | listJobs(String marker, int maxItemCount) | 列举Job状态信息 |
|  | *Task相关* | |
| 1. | listTasks(String jobId,String marker, int maxItemCount) | 列举一个job下所有task的状态信息 |
| 2. | getTask(String jobId, String taskName) | 获取task状态信息 |
|  | *Instance相关* | |
| 1. | listInstances(String jobId, String taskName, String marker, int maxItemCount) | 获取task状态信息 |
| 2. | getInstance(String jobId, String taskName) | 获取 instance 状态信息 |
|  | *Image相关* | |
| 1. | listImages(String marker, int maxItemCount) | 列举Images |
| 2. | getImage(String imageId) | 获取 Image 信息 |
| 2. | deleteImage(String imageId) | 删除Image |
| 2. | createImage(ImageDescription imageDescription) | 创建Image |


### 5. release note

4.7.0
```
1. 增加幂等token
```

4.6.0
```
1. AutoCluster增加竞价策略属性。
```

4.5.0
```
1. 集群增加竞价策略属性。
```

4.3.0

```
1. Mounts增加 cacheSupport 属性。
2. AutoCluster 增加 reserveOnFail 属性。
3. Group 增加Disks属性。
```

