# mysq_ruby_app_kubernetes

1) create the mysql database deployment  
#  kubectl create -f ruby_mysql.yaml
root@ip-172-31-27-115:/opt/git-repo#  kubectl get deployment
NAME            DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
ruby-mysql      1         1         1            0           55m

2) create the mysql service 
# kubectl create -f ruby_mysql_service.yaml
root@ip-172-31-27-115:/opt/git-repo# kubectl get svc
NAME            TYPE           CLUSTER-IP       EXTERNAL-IP         PORT(S)        AGE
kubernetes      ClusterIP      100.64.0.1       <none>              443/TCP        3d
ruby-mysql      ClusterIP      100.65.151.154   <none>              3306

3) Create the ruby on rails application deployment 
# kubectl create -f ruby_on_rails_deployment.yaml
root@ip-172-31-27-115:/opt/git-repo# kubectl get deployment
NAME            DESIRED   CURRENT   UP-TO-DATE   AVAILABLE   AGE
ruby-mysql      1         1         1            1           58m
ruby-on-rails   2         2         2            2           51m

4) Create the application service 
# kubectl create -f ruby_on_rails_service.yaml
root@ip-172-31-27-115:/opt/git-repo# kubectl get svc
NAME            TYPE           CLUSTER-IP       EXTERNAL-IP                                                              PORT(S)        AGE
kubernetes      ClusterIP      100.64.0.1       <none>                                                                   443/TCP        3d
ruby-mysql      ClusterIP      100.65.151.154   <none>                                                                   3306/TCP       56m
ruby-on-rails   LoadBalancer   100.71.77.185    a53af5256b25d11e8b01c024d7d2f3e8-91475347.ap-south-1.elb.amazonaws.com   80:32371/TCP   49m
  
  
  
  
