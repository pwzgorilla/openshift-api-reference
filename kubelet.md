+ pods
  - [GET /pods](#list-all-pods) *List all Pods*
+ stats
  - [GET /stats/summary](#status-summary) *Stats Summary*
  - [GET /stats/container](#stats-container) *Stats Container*
  - [GET /stats/{podName}/{containerName}](#stats-pod-container) *Stats Pod Container* 
  - [GET /stats/{namespace}/{podName}/{uid}/{containerName}](#stats-namespace-pod-container) *Stats Namespace Pod Container*
+ metrics
  - [GET /metrics](#metrics) *Metrics*

#### List all Pods
```
GET /pods
```
Example Request:
```
curl -k --cert ca.crt --key ca.key -H "Authorization: Bearer RkEutR0D1t_mXvseQIDzU9u084hcF3sj39G9QpoYVa4" https://127.0.0.1:10250/pods
```
Example Response:
```
{
    "kind":"PodList",
    "apiVersion":"v1",
    "metadata":Object{...},
    "items":[
        {
            "metadata":{
                "name":"logging-fluentd-t2hb4",
                "generateName":"logging-fluentd-",
                "namespace":"logging",
                "selfLink":"/api/v1/namespaces/logging/pods/logging-fluentd-t2hb4",
                "uid":"f138a94c-2b6a-11e8-8e25-0050568530fd",
                "resourceVersion":"4194936",
                "creationTimestamp":"2018-03-19T11:44:54Z",
                "labels":Object{...},
                "annotations":Object{...},
                "ownerReferences":Array[1]
            },
            "spec":{
                "volumes":Array[11],
                "containers":Array[1],
                "restartPolicy":"Always",
                "terminationGracePeriodSeconds":30,
                "dnsPolicy":"ClusterFirst",
                "nodeSelector":Object{...},
                "serviceAccountName":"aggregated-logging-fluentd",
                "serviceAccount":"aggregated-logging-fluentd",
                "nodeName":"master237.openshift.dataman",
                "securityContext":Object{...},
                "imagePullSecrets":Array[1],
                "schedulerName":"default-scheduler",
                "tolerations":Array[2]
            },
            "status":{
                "phase":"Running",
                "conditions":Array[3],
                "hostIP":"192.168.1.237",
                "podIP":"10.128.0.140",
                "startTime":"2018-03-19T11:44:54Z",
                "containerStatuses":Array[1],
                "qosClass":"BestEffort"
            }
        }
    ]
}
```

#### Status Summary
```
GET /stats/summary
```
Example Request
```
curl -k --cert ca.crt --key ca.key -H "Authorization: Bearer RkEutR0D1t_mXvseQIDzU9u084hcF3sj39G9QpoYVa4" https://127.0.0.1:10250/status/summary
```
Example Response
```
{
    "node":{
        "nodeName":"master237.openshift.dataman",
        "systemContainers":Array[2],
        "startTime":"2018-03-26T03:05:05Z",
        "cpu":Object{...},
        "memory":Object{...},
        "fs":Object{...},
        "runtime":Object{...}
    },
    "pods":[
        {
            "podRef":Object{...},
            "startTime":"2018-04-18T07:46:28Z",
            "containers":[
                {
                    "name":"dmos-oc-daemonset-ui-console",
                    "startTime":"2018-04-18T07:46:38Z",
                    "cpu":Object{...},
                    "memory":Object{...},
                    "rootfs":Object{...},
                    "logs":Object{...},
                    "userDefinedMetrics":null
                }
            ],
            "volume":Array[1]
        }
    ]
}
```

#### Stats Container
```
GET /stats/container
```
Example Request
```
curl -k --cert ca.crt --key ca.key -H "Authorization: Bearer RkEutR0D1t_mXvseQIDzU9u084hcF3sj39G9QpoYVa4" https://127.0.0.1:10250/stats/container
```
Example Response
```
{
    "/":{
        "name":"/",
        "subcontainers":Array[4],
        "spec":Object{...},
        "stats":[
            {
                "timestamp":"2018-04-20T11:25:10.687349402+08:00",
                "cpu":{
                    "usage":{
                        "total":"4547730774665154",
                        "per_cpu_usage":Array[8],
                        "user":3217831890000000,
                        "system":796544110000000
                    },
                    "cfs":Object{...},
                    "load_average":0
                },
                "diskio":Object{...},
                "memory":Object{...},
                "network":Object{...},
                "filesystem":Array[3],
                "task_stats":Object{...}
            }
        ]
    }
}
```
#### Stats Pod Container
```
GET /stats/{podName}/{containerName}
```
Example Request
```
curl -k --cert ca.crt --key ca.key -H "Authorization: Bearer RkEutR0D1t_mXvseQIDzU9u084hcF3sj39G9QpoYVa4" https://127.0.0.1:10250/stats/dmos-oc-daemonset-ui-7r6gl/dmos-oc-daemonset-ui-console
```
Example Response
```
{
    "id":"63870e4d8242e92c73e8fb2379955d4ddcefd8d5ea85387cb312bc4cce9b9e0f",
    "name":"/kubepods.slice/kubepods-burstable.slice/kubepods-burstable-pod9806837c_42dc_11e8_9a3f_0050568530fd.slice/docker-63870e4d8242e92c73e8fb2379955d4ddcefd8d5ea85387cb312bc4cce9b9e0f.scope",
    "aliases":Array[2],
    "namespace":"docker",
    "labels":Object{...},
    "spec":Object{...},
    "stats":[
        {
            "timestamp":"2018-04-20T11:36:06.713688484+08:00",
            "cpu":{
                "usage":Object{...},
                "cfs":Object{...},
                "load_average":0
            },
            "diskio":{
                "io_service_bytes":Array[4],
                "io_serviced":Array[4]
            },
            "memory":{
                "usage":5660672,
                "cache":4030464,
                "rss":1630208,
                "swap":0,
                "working_set":3162112,
                "failcnt":0,
                "container_data":Object{...},
                "hierarchical_data":Object{...}
            },
            "network":{
                "name":"",
                "rx_bytes":0,
                "rx_packets":0,
                "rx_errors":0,
                "rx_dropped":0,
                "tx_bytes":0,
                "tx_packets":0,
                "tx_errors":0,
                "tx_dropped":0,
                "tcp":Object{...},
                "tcp6":Object{...}
            },
            "filesystem":[
                Object{...}
            ],
            "task_stats":{
                "nr_sleeping":0,
                "nr_running":0,
                "nr_stopped":0,
                "nr_uninterruptible":0,
                "nr_io_wait":0
            }
        }
    ]
}
```
#### Stats Namespace Pod Container
```
GET /stats/{namespace}/{podName}/{uid}/{containerName}
```
Example Request
```
curl -k --cert ca.crt --key ca.key -H "Authorization: Bearer RkEutR0D1t_mXvseQIDzU9u084hcF3sj39G9QpoYVa4" https://127.0.0.1:10250/stats/default/dmos-oc-daemonset-ui-7r6gl/9806837c-42dc-11e8-9a3f-0050568530fd/dmos-oc-daemonset-ui-console
```
Example Response
```
{
    "id":"63870e4d8242e92c73e8fb2379955d4ddcefd8d5ea85387cb312bc4cce9b9e0f",
    "name":"/kubepods.slice/kubepods-burstable.slice/kubepods-burstable-pod9806837c_42dc_11e8_9a3f_0050568530fd.slice/docker-63870e4d8242e92c73e8fb2379955d4ddcefd8d5ea85387cb312bc4cce9b9e0f.scope",
    "aliases":Array[2],
    "namespace":"docker",
    "labels":Object{...},
    "spec":{
        "creation_time":"2018-04-18T15:46:38.700847154+08:00",
        "labels":Object{...},
        "has_cpu":true,
        "cpu":Object{...},
        "has_memory":true,
        "memory":Object{...},
        "has_network":false,
        "has_filesystem":true,
        "has_diskio":true,
        "has_custom_metrics":false,
        "image":"devharbor.dataman-inc.com:1443/jborg-dev/dmos-oc-ui@sha256:4d90451567e5e489bb045f8e9d0d08caea74d1920840082eb374213a0eb8ea16"
    },
    "stats":[
        {
            "timestamp":"2018-04-20T11:45:57.226280847+08:00",
            "cpu":Object{...},
            "diskio":Object{...},
            "memory":Object{...},
            "network":Object{...},
            "filesystem":Array[1],
            "task_stats":Object{...}
        }
    ]
}
```
#### Metrics
```
GET /metrics
```
