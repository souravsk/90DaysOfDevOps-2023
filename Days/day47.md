# AWS CodePipeline

*On this last day of AWS services we are going to talk about a big one that has a lot of moving parts and integrations. There are a few free resources out there that will help in your learning/understanding of this... but honestly some of the best ones will cost you some money. I will list them out seperately in the resources section and call them out, but I would be remiss in NOT mentioning them as they are fantastic for learning this complex service*

**CodePipeline** is a fully managed continuous delivery service that allows you to automate your IaC or software release processes. It enables you to create pipelines that build, test, and deploy your code changes continuously and (with proper testing in place) reliably:

![https://github.com/MichaelCade/90DaysOfDevOps/raw/main/2023/images/day55-01.jpg](https://github.com/MichaelCade/90DaysOfDevOps/raw/main/2023/images/day55-01.jpg)

With CodePipeline, you can create pipelines that automate your build, test, and deployment workflows, ensuring that your code changes are reliably deployed to your target environments. It enables you to achieve faster release cycles, improve collaboration among development and operations teams, and improve the overall quality and reliability of your software releases.

AWS CodePipeline integrates with other AWS services:

- [Source Action Integrations](https://docs.aws.amazon.com/codepipeline/latest/userguide/integrations-action-type.html#integrations-source)
- [Build Action Integrations](https://docs.aws.amazon.com/codepipeline/latest/userguide/integrations-action-type.html#integrations-build)
- [Test Action Integrations](https://docs.aws.amazon.com/codepipeline/latest/userguide/integrations-action-type.html#integrations-test)
- [Deploy Action Integrations](https://docs.aws.amazon.com/codepipeline/latest/userguide/integrations-action-type.html#integrations-deploy)
- [Approval Action Integrations](https://docs.aws.amazon.com/codepipeline/latest/userguide/integrations-action-type.html#integrations-approval)
- [Invoke Action Integrations](https://docs.aws.amazon.com/codepipeline/latest/userguide/integrations-action-type.html#integrations-invoke)

It also integrates with third-party tools such as GitHub, Jenkins, and Bitbucket. You can use AWS CodePipeline to manage your application updates across multiple AWS accounts and regions.

## Getting started with AWS CodePipeline

To get started with AWS CodePipeline, there are several excellent [tutorials](https://docs.aws.amazon.com/codepipeline/latest/userguide/tutorials.html) in the [AWS User Guide](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html). They all basically break down into the following 3 steps:

### Step 1: Create an IAM role

You need to create an IAM role that allows AWS CodePipeline to access the AWS resources required to run your pipelines. To create an IAM role, review the steps from [Day 52](https://github.com/MichaelCade/90DaysOfDevOps/blob/main/2023/day52.md)

### Step 2: Create a CodePipeline pipeline

To create a CodePipeline pipeline, go to the AWS CodePipeline console, click on the "Create pipeline" button, and then follow the instructions to create your pipeline. You will need to specify the source location for your code, the build provider you want to use, the deployment provider you want to use, and the IAM role you created in step 2.

### Step 3: Test and deploy your code changes

Once you have created your CodePipeline pipeline, you can test and deploy your code changes. AWS CodePipeline will automatically build, test, and deploy your code changes to your target environments. You can monitor the progress of your pipeline in the AWS CodePipeline console.

## Capstone Project

To tie up this AWS section of the 90 Days of DevOps, I recommend that you go through Adrian Cantrill's excellent mini-project, the [CatPipeline](https://www.youtube.com/playlist?list=PLTk5ZYSbd9MgARTJHbAaRcGSn7EMfxRHm). In it you will be exposed to CodeCommit, CodeBuild, CodeDeploy, and CodePipeline in a fun little project that will give you a taste of a day in the life of a DevOps engineer.

- [YouTube CatPipeline Playlist](https://www.youtube.com/playlist?list=PLTk5ZYSbd9MgARTJHbAaRcGSn7EMfxRHm)
- [GitHub CatPipeline Repo](https://github.com/acantril/learn-cantrill-io-labs/tree/master/aws-codepipeline-catpipeline)