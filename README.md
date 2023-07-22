# Practice3.5
# Assignment3.5

## Steps of creating image and deployed to AWS ECR

### Pre-requisites and Authentication to ECR (private repository)
- if using Windows or Mac:
    Run 
    ```sh
    aws configure
    ```
    on terminal / command prompt to configure your Access and Secret access keys with at least AmazonEC2ContainerRegistryPowerUser permissions
- if using EC2:
    Attach IAM role with AmazonEC2ContainerRegistryPowerUser permissions to the EC2 

- Run
    ```sh
    aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin <aws account number>.dkr.ecr.ap-southeast-1.amazonaws.com
    ```
    on terminal.

- Login to AWS Console and grant the uer with IAM Policy as below:
    AmazonEC2ContainerRegistryPowerUser 

### Creation of repository in AWS ECR

- Step1:  Login to AWS console with username and password. 
- Step2: Search for AWS ECR.
- Step3: On the front page, click on "Repository" under AWS ECR on the left plane.
- Step4: Click on "Create Repository"
- Step5: As default setting and name the repository.

### Creation of repository in Github

- Step 1: Login to Github with username and password. 
- Step 2: Click on "New repository" on the upper-right corner plus sign.
- Step 3: Name the repository name under repository name. 
- Step 4: Optionally, add a description of the repository, etc "for AWS ECR imag"
- Step 5: Choose a repository visibility, either "Private" or "Public".
- Step 6: Select Initialize this repository with a README.
- Step 7: Click Create repository.

### Creation of image using Visual Code

#### In Visual Code terminal, run the following comemnds. 

#### 1. Command to build an image
        ```sh
        docker build -t <IMAGE_NAME>:<IMAGE_TAG> .
        ```
#### 2. Command exmaple with the image
         ```sh
        docker build -t simple-app-image .
        ```
#### 3. Command to tag an image
        ```sh
        docker tag <IMAGE_NAME>:<IMAGE_TAG>  <REPOSITORY_URI>:<IMAGE_TAG>
        ```
#### 4. Command example with our image and repository
        ```sh
        docker tag simple-app-image:latest <account no.>.dkr.ecr.ap-southeast-1.amazonaws.com/<REPOSITORY_NAME>:latest
        ```
#### 5. Command to retrieve an authentication token and authenticate your Docker client to your registry.
        ```sh
        aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin 255945442255.dkr.ecr.ap-southeast-1.amazonaws.com
        ```
#### 6.Command to push image
        ```sh
        docker push <account no.>.dkr.ecr.ap-southeast-1.amazonaws.com/<REPOSITORY_NAME>:latest
        ```

