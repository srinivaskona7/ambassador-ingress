# ambassador-ingress

# URL for ambassador controller process

https://www.getambassador.io/docs/kubernetes/latest/howtos/codetocluster/

# Add the Repo:
helm repo add datawire https://www.getambassador.io
 
# Create Namespace and Install:
kubectl create namespace ambassador && \
helm install ambassador --namespace ambassador datawire/ambassador && \
kubectl -n ambassador wait --for condition=available --timeout=90s deploy -lproduct=aes

# with kubectl command

kubectl apply -f https://www.getambassador.io/yaml/aes-crds.yaml && \
kubectl wait --for condition=established --timeout=90s crd -lproduct=aes && \
kubectl apply -f https://www.getambassador.io/yaml/aes.yaml && \
kubectl -n ambassador wait --for condition=available --timeout=90s deploy -lproduct=aes

# create tls secret

kubectl create secret tls ingress --key private.key --cert certificate.crt

# docker  secret 

kubectl create secret docker-registry dockersecret  --docker-username=** --docker-password=**

# command to create kubernetes objects

kubectl apply -f deploy.yaml  host.yaml
