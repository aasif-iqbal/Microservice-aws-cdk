## Microservice cdk setup

1. Download aws cli
```
https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html

https://awscli.amazonaws.com/AWSCLIV2.pkg

> which aws
/usr/local/bin/aws

> aws --version
```

2. Install aws cdk
```
sudo npm install -g aws-cdk
cdk --version
```

3. Now, we need to setup IAM-USER in aws-account.
  a. Login to aws-account. (iam-user)
  b. Create-group > Access Management > User groups
    Name: cdk-dev-local
    click-btn: create group

  c. Create-user > Access Management > Users > Add User
    user name: cdk-aasif-local
    clicl-btn: next

  d. Set Permission
    (*)Add user group

    User group 
    Group name > cdk-aasif-local > next > create user

  e. IAM > User group
    click on - cdk-dev-local

    Users|Permission (click)|  

    Add Permission > attach polices

    type `admin` in search box 
    [checked] Administrator access  > Add Permission
    Policy name - Administrator access

  f. IAM > Users > cdk-aasif-local
    click - cdk-aasif-local
    Permission| Group|tags|security credential (click)
    Access key -> create access key -> Command line interface(CLI)
    set description tag: cdk-local-access 
    click-btn: create access key

    copy:
    access-key: AKIA...............KKM
    secret-access-key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

4. Open termincal at root dir.
```
aws config
Aws Access keyID:
Aws Secret access key:
Default region name:
Default output format(json):
```

5. Open terminal at project dir.
  a. create project folder - mkdir Product-services
  b. cd Product-services
  c. cdk init app --language=typescript

6. Project Structure is created.
  Product-services 
    - bin
    - lib/product-services-stack.ts (infra-structure as a code) 
    - src/index.ts (Lambda handler function) [we need to create `src` folder manually]

7. After setup `lib/product-services-stack.ts` and write code in `src/index.ts`.

8. Open terminal at Product-services.
```
Product-services> cdk-bootstrap
```
Note: Make sure you have installed `docker-desktop` & it must be running on background during `cdk-bootstrap`

9. Goto AWS-CloudFormation (website)
stacks  - CDKToolkit(stack-name)

10. Open terminal at Product-services.
```
Product-services> cdk synth
Product-services> cdk deploy --verbose --trace
Do you wish to deploy these changes(y/n)? Y
```

11. Output:
```
ProductServiceStack = https://5m...UKXOex.............com/prod/
```

----------------------------------------------------------------------------------

npm install --save-dev @types/aws-lambda
