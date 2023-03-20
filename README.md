## Accessing AWS Secret Manager's data from microservices deployed on kubernetes cluster.

### step 1: Create a secret in AWS secret manager.
    
       ![aws secret manager data.]
       (https://github.com/manishk1001/kube_csi-driver/blob/main/Screenshots/1.png)


### step 2: Create the policy and IAM rule for accessing the secret in secret manager and downloading the ACCESS_KEYS
 



### Step 3: storing Access key and secret access key in kubernetes secret.
          
### step 4: installing External Secret Operator using helm.


helm repo add external-secrets https://charts.external-secrets.io

helm install external-secrets \
   external-secrets/external-secrets \
    -n external-secrets \
    --create-namespace \
   --set installCRDs=true
        
### step 5: create kind: SecretStore using secret-store.yaml
    Create kind: ExternalSecret using external-secret.yaml
    kubernetes secret with the name my-secret will automatically be created which will
    be in sync with the data present in aws secret manager.
        
### step 6: consider the newly created "my-secret" as normal kubernetes secret and pass the my-secret data to the required microservice as Environment variable.
