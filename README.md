# actions-demo

# Requirements:

A Cloud Guru Account with access to AWS Cloud Sandbox

# Steps:
1. Launch an AWS Sandbox environment via learn.acloud.guru/cloud-playground/cloud-sandboxes
2. Retrieve the Access Key ID and Secret Access Key
3. Use the ssh-keygen command in Windows, Mac or Linux to create RSA keypairs, name it actions-demo, this will generate a private key and public key
4. In your actions-demo fork, go to settings > secrets and variables > actions:
    - click the "New repository secret" button and create new secrets with the following:
        1. Access Key ID 
            - Name: ACCESS_KEY
            - Secret: Access Key ID from step 2
        2. Secret Access Key
            - Name: SECRET_KEY
            - Secret: Secret Access Key from step 2
        3. SSH Public Key
            - Name: SSH_PUBLIC_KEY
            - Secret: Contents of actions-demo.pub file from step 3
        4. SSH Private Key
            - Name: SSH_PRIVATE_KEY
            - Secret: Contents of actions-demo file from step 3
    - click on the variables tab, then click on the "New repository variable" button and create a new variable with:
        1. Region
            - Name: REGION
            - Value: us-east-1
5. Go to the actions tab on the repo
6. Click on "Run workflow"
7. Once completed, view the Run playbook, go to the bottom of the log and connect to the ip address that's under the PLAY RECAP
