We are following the instructions on this github repo.

https://github.com/piyushsachdeva/CKA-2024/tree/main/Resources/Day-50-Operators

We are now in step 4: doing this -

# Install OLM
curl -sL https://github.com/operator-framework/operator-lifecycle-manager/releases/download/v0.32.0/install.sh | bash -s v0.32.0

# Install the operator
kubectl create -f https://operatorhub.io/install/cert-manager.yaml

kubectl get pods -n olm

kubectl get csv -n operators

kubectl get pods -n operators

kubectl get crds | grep cert-manager

kubectl apply -f cert-manager-operatorgroup.yaml

kubectl get issuer -n default
kubectl get certificate -n default

kubectl apply -f selfsigned-issuer.yaml

kubectl get issuer selfsigned-issuer -n default

kubectl apply -f my-app-certificate.yaml

kubectl get certificate my-app-certificate -n default

kubectl get secret my-app-tls -n default

kubectl logs -f -n operators $(kubectl get pods -n operators -l app.kubernetes.io/component=controller -o jsonpath='{.items[0].metadata.name}')

kubectl get pods -n operators -l app.kubernetes.io/component=controller

kubectl delete pod <cert-manager-controller-pod-name> -n operators

kubectl delete -f my-app-certificate.yaml
kubectl delete -f selfsigned-issuer.yaml

kubectl delete -f cert-manager-subscription.yaml
kubectl delete -f cert-manager-operatorgroup.yaml

kubectl delete namespace operators

kubectl delete namespace olm