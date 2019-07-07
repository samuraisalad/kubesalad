
```
cd ecsdemo-nodejs
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
```

```
cd ecsdemo-crystal
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
```

### ELBサービスロールがなければ作成
```
aws iam get-role --role-name "AWSServiceRoleForElasticLoadBalancing" || aws iam create-service-linked-role --aws-service-name "elasticloadbalancing.amazonaws.com"
```

```
cd ecsdemo-frontend
kubectl apply -f kubernetes/deployment.yaml
kubectl apply -f kubernetes/service.yaml
```

```
CURRENT=`pwd`
cd $CURRENT/ecsdemo-frontend
kubectl delete -f kubernetes/service.yaml
kubectl delete -f kubernetes/deployment.yaml

cd $CURRENT/ecsdemo-crystal
kubectl delete -f kubernetes/service.yaml
kubectl delete -f kubernetes/deployment.yaml

cd $CURRENT/ecsdemo-nodejs
kubectl delete -f kubernetes/service.yaml
kubectl delete -f kubernetes/deployment.yaml
```
