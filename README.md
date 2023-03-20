## Managing Kubernetes secrets with AWS Secrets Manager using External Secrets Operator.

### step 1: Create a secret in AWS Secrets Manager.
![2](https://user-images.githubusercontent.com/61675371/226323040-327cdbe6-3ed6-4c92-87eb-9b62b3840a3d.png)

### step 2: Create the policy and IAM role for accessing the secret in Secrets Manager and downloading the ACCESS_KEYS
![3](https://user-images.githubusercontent.com/61675371/226323183-69d9bc6b-4681-46d9-bb75-08e1e4e55be8.png)

### Step 3: Storing Access key and secret access key in Kubernetes secret.
![1](https://user-images.githubusercontent.com/61675371/226323296-9ef0ebf0-ac39-412a-a589-915d2b806d5d.png)

### step 4: Installing External Secret Operator using helm.



      helm repo add external-secrets https://charts.external-secrets.io

      helm install external-secrets \
      external-secrets/external-secrets \
           -n external-secrets \
           --create-namespace \
           --set installCRDs=true
        
### step 5: Create "kind: SecretStore" using secret-store.yaml
![4](https://user-images.githubusercontent.com/61675371/226323645-3657714d-1f90-40ba-a170-2215feb4d491.png)

Create "kind: ExternalSecret" using external-secret.yaml

![5](https://user-images.githubusercontent.com/61675371/226323874-038fcb63-3738-473e-80be-9c27014d0136.png)

kubernetes secret with the name "my-secret" will automatically be created which will be in sync with the data present in aws secret manager.

![6](https://user-images.githubusercontent.com/61675371/226324087-d0aa87c3-9faf-4b04-8ac4-7eba672e0b17.png)
    
        
### step 6: Consider the newly created "my-secret" as normal kubernetes secret and pass the "my-secret" data to the required microservice as Environment variable or as Volume.
