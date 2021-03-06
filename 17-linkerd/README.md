# LinkerD Service Mesh

* Download linkerd CLI: https://linkerd.io/2/getting-started/#step-1-install-the-cli
* Check if everything is correct for LinkerD
* For Kubernetes >=1.17.0 the Clock Skew error can be ignored

```sh
linkerd check --pre
```

* Install LinkerD

```sh
linkerd install | kubectl apply -f -
```

* Edit hostnames in `linkerd-ingress.yaml`
* Add Ingress for LinkerD dashboard

```sh
kubectl apply -f basic-auth.yaml
kubectl apply -f linkerd-ingress.yaml
```

* Inject LinkerD proxy into existing deployments

Add this anntation to pods

```sh
linkerd.io/inject: enabled
```

Or run

```sh
kubectl get deployments -o yaml | linkerd inject - | kubectl apply -f -
```

* Check LinkerD dashboard
