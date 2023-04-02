# Deploy to AWS using Ansible and GitHub Actions

As the title suggests this shows one of the ways to use ansible and GitHub actions to deploy to AWS.
We recommend watching the [recording](https://web.microsoftstream.com/video/d4ef98e4-24c7-41a7-805e-a90b3bc3201c?channelId=db8f45af-595e-4810-a7f1-34abf4e36b0e) before you start trying this out!. As we are using a 3rd party action, please read the disclaimer in the footnotes[^disclaimer].

NB: We have added a zip file for easy download of the source files, click [this link](all_demo_source_files.zip) and select the download button in the next page.[^caveat]

# Requirements:

- A Cloud Guru Account with access to AWS Cloud Sandbox
- access to a Github account
- Generate your own set of SSH keys (we recommend using a separate key pair as good practise)

## How to generate SSH keys?

1. Use the "ssh-keygen" command in Windows (command prompt) or Mac/Linux Terminal to create RSA SSH keypairs.
2. When it prompts you for the name, enter "actions-demo", this will generate a private key and public key pair. 
3. The private key will be called "actions-demo", and the public key will be called "actions-demo.pub". Please skip entering a password/passphrase for the purposes of the demo for the key pair. For further reference see [this link](https://www.digitalocean.com/community/tutorials/how-to-create-ssh-keys-with-openssh-on-macos-or-linux).

# Steps:
1. Launch an AWS Sandbox environment via learn.acloud.guru/cloud-playground/cloud-sandboxes
2. Retrieve the Access Key ID and Secret Access Key from the new page, this will be used later in step 5 for the secrets.
3. Use the ssh-keygen command in Windows, Mac or Linux to create RSA key pairs, name it actions-demo, this will generate a private key and public key
4. Create a new git repository and upload the files/folders from here. The important folders are .github/workflows & ansible. (We are aware that during the demo it was suggested to fork the repo. But given these arctifacts here are part of the lager DevOps Guild repo it's easier if you create your own repo. The steps below will work either way as long as this is run from a GitHub repository.)
5. In your in new repo, go to settings > secrets and variables > actions ( [see screenshots in Appendix](#Appendix) ):
    - click the "New repository secret" button and create new secrets with the following:
        1. Access Key ID 
            - Name: ACCESS_KEY
            - Secret: Access Key ID from step 2 (AWS Sandbox Environment in A Cloud Guru)
        2. Secret Access Key
            - Name: SECRET_KEY
            - Secret: Secret Access Key from step 2 (AWS Sandbox Environment in A Cloud Guru)
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
6. Go to the actions tab on the repo
7. Click on "Run workflow"
8. Once completed, view the Run playbook, go to the bottom of the log and connect to the ip address that's under the PLAY RECAP

# Questions
If you have questions please reach out to [Leon Ng](mailto:leon.ng@capgemini.com) or [Yacko Abrams](yacko.abrams@capgemini.com)


[^disclaimer]: The GitHub actions featured here uses a third party action from the marketplace. Please DON'T use this third party action on a client project. Please use your own hosted GitHub runner ([check this for details](https://docs.github.com/en/actions/using-github-hosted-runners/about-github-hosted-runners)). The 3rd party action was used for making the demo easier to run.
[^caveat]: This contents of the Zip needs to be placed at the root of your Github Repository.
