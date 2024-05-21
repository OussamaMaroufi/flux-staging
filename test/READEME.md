### SECURITY

kube Api server ---- ETCD
- In kubeconfig file we find PKI cert that's defines our users
- Users are just PKI signed Certificate

- Some App needs to access api server
- we can do that using serviceAccount
- In order to have access we need to to be connected to a ROlE OR CLUSTEROLE   we use RoleBinding ,or clusterRoleBinding

* Security Context
- It defines privilege and access control settings for pod
- it can be set at container level or pod level
  ```
  kubectl explain pod.spec.securityContext
  ```
  ```
  kubectl explain pod.spec.containers.securityContext
  ```
  - low level win means containers if priv defined twice .

     - Every has a default service account assinged to it
     - Run a pod and exec inside it
     - kubectl exec -it podName -- sh
     - check the priv:
     - curl https://kubernetes/api/v1 --insecure
   
  * Authenticate users in k8s
-  Auth mechanisme  - Basic
prepare a csv file containe usernam,pwd,userId
in pod kube-api-server add this line
- --basic-auth-file=user-dettails.csv
- and then restart the pod
- to authenticate : curl -v -k apiserverUrl/api/v1/pods -u "user1:passwors1"

![image](https://github.com/OussamaMaroufi/flux-staging/assets/93825558/70f18e80-97fe-4e5a-b111-a1ef8c4cf4e3)

  
  
