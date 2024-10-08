# Task 2: Manage Kubernetes Pods and Services

1. Get the list of pods  
    ```shell
    kubectl get pods
    #output
    NAME                             READY   STATUS    RESTARTS   AGE
    my-deployment1-68bcd84fd-ljjql   1/1     Running   0          4m34s
    ```
    
    This command displays all pods, including those created by the my-deployment1 Deployment.

2. Show labels

    Replace `<pod-name>` with the actual pod Name:
    
    ```shell
    kubectl get pod <pod-name> --show-labels
    #output
    NAME                             READY   STATUS    RESTARTS   AGE     LABELS
    my-deployment1-68bcd84fd-ljjql   1/1     Running   0          7m55s   app=my-deployment1,pod-template-hash=68bcd84fd
    ```
    
    This command will list the labels associated with the specified pod, helping you identify its attributes and categorization within your Kubernetes cluster.

3. Label the pod  

    Replace `<pod-name>` with the actual pod Name:
    
    ```shell
    kubectl label pods <pod-name> environment=deployment
    #output
    pod/my-deployment1-68bcd84fd-ljjql labeled
    ```
    
    The command is used in Kubernetes to label a specific pod with the key-value pair `environment=deployment`. This label helps categorize and manage pods based on their deployment environment, making it easier to organize and select Kubernetes objects within the cluster.

4. Show labels  

    Replace `<pod-name>` with the actual pod Name:
    
    ```shell
    kubectl get pod <pod-name> --show-labels
    #output
    NAME                             READY   STATUS    RESTARTS   AGE     LABELS
    my-deployment1-68bcd84fd-ljjql   1/1     Running   0          9m54s   app=my-deployment1,enviroment=deployment,pod-template-hash=68bcd84fd
    ```

5. Run a test pod using the nginx image  

    ```shell
    kubectl run my-test-pod --image=nginx --restart=Never
    #output
    pod/my-test-pod created
    ```
    
    This command tells Kubernetes to create a pod named "my-test-pod" using the nginx image, and the pod will not restart automatically if it stops for any reason as we are using `--restart=Never`.

6. Show logs  

    Replace `<pod-name>` with the actual name of the pod:
    
    ```shell
    kubectl logs <pod-name>
    #output
    /docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
    /docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
    /docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
    10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
    10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
    /docker-entrypoint.sh: Sourcing /docker-entrypoint.d/15-local-resolvers.envsh
    /docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
    /docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
    /docker-entrypoint.sh: Configuration complete; ready for start up
    2024/09/02 20:08:40 [notice] 1#1: using the "epoll" event method
    2024/09/02 20:08:40 [notice] 1#1: nginx/1.27.1
    2024/09/02 20:08:40 [notice] 1#1: built by gcc 12.2.0 (Debian 12.2.0-14) 
    2024/09/02 20:08:40 [notice] 1#1: OS: Linux 5.4.0-193-generic
    2024/09/02 20:08:40 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
    2024/09/02 20:08:40 [notice] 1#1: start worker processes
    2024/09/02 20:08:40 [notice] 1#1: start worker process 29
    2024/09/02 20:08:40 [notice] 1#1: start worker process 30
    2024/09/02 20:08:40 [notice] 1#1: start worker process 31
    2024/09/02 20:08:40 [notice] 1#1: start worker process 32
    2024/09/02 20:08:40 [notice] 1#1: start worker process 33
    2024/09/02 20:08:40 [notice] 1#1: start worker process 34
    2024/09/02 20:08:40 [notice] 1#1: start worker process 35
    2024/09/02 20:08:40 [notice] 1#1: start worker process 36
    2024/09/02 20:08:40 [notice] 1#1: start worker process 37
    2024/09/02 20:08:40 [notice] 1#1: start worker process 38
    2024/09/02 20:08:40 [notice] 1#1: start worker process 39
    2024/09/02 20:08:40 [notice] 1#1: start worker process 40
    2024/09/02 20:08:40 [notice] 1#1: start worker process 41
    2024/09/02 20:08:40 [notice] 1#1: start worker process 42
    2024/09/02 20:08:40 [notice] 1#1: start worker process 43
    2024/09/02 20:08:40 [notice] 1#1: start worker process 44
    ```

    This command retrieves and displays the logs generated by the specified pod, allowing you to troubleshoot issues, monitor activity, and gather information about the pod's behavior.