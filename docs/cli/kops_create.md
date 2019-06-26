
<!--- This file is automatically generated by make gen-cli-docs; changes should be made in the go CLI command code (under cmd/kops) -->

## kops create

Create a resource by command line, filename or stdin.

### Synopsis

Create a resource:
  
  * cluster  
  * instancegroup  
  * secret  

Create a cluster, instancegroup or secret using command line parameters, YAML configuration specification files, or stdin. (Note: secrets cannot be created from YAML config files yet).

```
kops create -f FILENAME [flags]
```

### Examples

```
  # Create a cluster from the configuration specification in a YAML file
  kops create -f my-cluster.yaml
  
  # Create secret from secret spec file
  kops create -f secret.yaml
  
  # Create an instancegroup based on the YAML passed into stdin.
  cat instancegroup.yaml | kops create -f -
  
  # Create a cluster in AWS
  kops create cluster --name=kubernetes-cluster.example.com \
  --state=s3://kops-state-1234 --zones=eu-west-1a \
  --node-count=2 --node-size=t2.micro --master-size=t2.micro \
  --dns-zone=example.com
  
  # Create an instancegroup for the k8s-cluster.example.com cluster.
  kops create ig --name=k8s-cluster.example.com node-example \
  --role node --subnet my-subnet-name
  
  # Create a new ssh public key called admin.
  kops create secret sshpublickey admin -i ~/.ssh/id_rsa.pub \
  --name k8s-cluster.example.com --state s3://example.com
```

### Options

```
  -f, --filename strings   Filename to use to create the resource
  -h, --help               help for create
```

### Options inherited from parent commands

```
      --alsologtostderr                  log to standard error as well as files
      --config string                    yaml config file (default is $HOME/.kops.yaml)
      --log_backtrace_at traceLocation   when logging hits line file:N, emit a stack trace (default :0)
      --log_dir string                   If non-empty, write log files in this directory
      --log_file string                  If non-empty, use this log file
      --log_file_max_size uint           Defines the maximum size a log file can grow to. Unit is megabytes. If the value is 0, the maximum file size is unlimited. (default 1800)
      --logtostderr                      log to standard error instead of files (default true)
      --name string                      Name of cluster. Overrides KOPS_CLUSTER_NAME environment variable
      --skip_headers                     If true, avoid header prefixes in the log messages
      --skip_log_headers                 If true, avoid headers when openning log files
      --state string                     Location of state storage (kops 'config' file). Overrides KOPS_STATE_STORE environment variable
      --stderrthreshold severity         logs at or above this threshold go to stderr (default 2)
  -v, --v Level                          number for the log level verbosity
      --vmodule moduleSpec               comma-separated list of pattern=N settings for file-filtered logging
```

### SEE ALSO

* [kops](kops.md)	 - kops is Kubernetes ops.
* [kops create cluster](kops_create_cluster.md)	 - Create a Kubernetes cluster.
* [kops create instancegroup](kops_create_instancegroup.md)	 - Create an instancegroup.
* [kops create secret](kops_create_secret.md)	 - Create a secret.
