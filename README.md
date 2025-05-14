# Terraform Associate Exam Important Topics
Terraform Associate Certification Tips

I have recently cleared the Terraform Associate Certification. Here are the steps you can follow to prepare effectively:

Questions to answer : 57
Type of questions expected: 
    a) True or False
    b) Multiple Choice questions
    c) Fill in the blanks. (Here you need to write terraform commands). 

1. Understand the core terraform workflow.
-> Here you need to understand how terraform workflow works. terraform init, terraform fmt, terraform plan, terraform apply, terraform destroy. This is the basic workflow of terraform.

2. Understand the purpose of terraform (v/s Other IAC Tools)
-> Here the person needs to understand the advantages of using Terraform over other tools. 
   For eg you will encounter something like this:
   What advantages does Terraform offer over using a provider's native tooling for deploying resources in multi-cloud environments? (select three)
   Options:
     a) Terraform can help businesses deploy applications on multiple clouds and on-premises infrastructure
     b) Terraform is not cloud-agnostic and can only be used to deploy resources across a single public cloud at a time
     c) Terraform can manage cross-cloud dependencies
     d) Terraform simplifies management and orchestration, helping operators build large-scale, multi-cloud infrastructure

3. Understand the Infrastructure as Code.
-> Here you need to understand how IAC is helping organizations in real world scenarios.

4. Interact with Terraform Modules.
-> Understand about modules and know where the modules are stored by default.
   Also how the value of one module can be referenced in another module.
   Example: A child module created a new subnet for some workloads. What terraform block allows to pass the value to parent module?
   Ans: Output block.
   
5. Implementing and maintaining the state.
-> Understand state locking and its importance in real-time.
   Example: If multiple developers are working on a same statefile, what remote feature is critical to ensure the state doesnot become corrupt?
   Ans: Statelocking
   Also remember that terrform statefile contains sensitive data. The statefile is stored in the current directory.

6.  Using Terraform Outside of Core workflow.
-> Here you expect the questions something like this:
   Mr.X is working on infrastructure manually and the company decided to move to IAC. So how can you ensure that existing resources are managed by terraform 
   without causing interruption to existing resources?
   Ans: Use terraform import.
   Note: Before terraform import we need to update the configuration file to include the new resources that matches the resources you want to import. 

7. Read, Generate and Modify the configuration.
-> Here you need to have the understanding of writing the terraform configuration files and what follows after which one. Go through how data block is used and how 
   it is used in real world scenarios.
   Example: Given a Terraform config that includes the following code, how would you reference the last instance that will be created?



resource "aws_instance" "database" {
  # ...
  for_each = {
    "vault": "secrets",
    "terraform": "infrastructure",
    "consul": "networking",
    "nomad": "scheduler"
  }
}

Ans: aws_instance.database["nomad"]

8. Understand Terraform Cloud Capabilities.
-> Here you can expect the concepts of Policy of Code. Questions on Terraform CLI vs Hashicorp Terraform can be expected and sentinel policy usecases can be 
   expected here.
   Example:
       a) What is the primary function of HCP Terraform agents?
       Ans: Execute Terraform plans and apply changes to the infrastructure.
       b) Which feature of HCP Terraform can be used to enforce fine-grained policies to enforce standardization and cost controls before resources are provisioned 
          with Terraform?
       Ans: Sentinel and OPA


Some important points to remember:

a) If you get a question on validating the configuration, modules and to report errors, then choose "terraform validate". 
b) Question on rewriting the config files to canonical format and style choose "terraform fmt".
c) To launch an interactive console to evaluate and experiment with expressions choose "terraform console".
d) A question on variable types in terraform. Here float is not a part of it.
e) Version ~> "1.35.0" . This only supports minor version change not major changes. 
   Means this supports version "1.35.2" not version "1.36.0".
f) Understand when to use "terraform apply -replace" and "terraform state rm".
g) A question switching or creating a terraform workspace. ( "terraform workspace new" to create, "terraform workspace select" to choose)   
h) What env variable can be set to enable detailed logging?
   Since it requires detailed logging, choose "TF_LOG" with TRACE is the most "VERBOSE" . Remember the word verbose here.
i) Commands to remember:
terraform init -upgrade : to initialise the configurations and modules to the latest version.
terraform plan -out=file_name : this saves the plan output to a particular file name.
terraform apply -replace : to mark the resource for replacement.
terraform plan -refresh-only : to refresh the state
terraform apply -destroy : to destroy the resources/
terraform plan -destroy : to generate the plan of destroying resources
terraform graph : for visual representation of a configuration.
