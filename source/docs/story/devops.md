# DevOps

In 2008, a conversation between Andrew Clay and Patrick Debois led to something quite revolutionary. While discussing 
the drawbacks of Agile, DevOps was born. After an event in Belgium the following year called "DevOpsDays," DevOps 
became the next buzzword, and its popularity increased.

| ![RedLine](../../_static/images/devops.png)
|:--:|
| DevOps is quite different from other methodologies because it focuses on driving "cultural change" to increase 
efficiency. |

It attempts to unite the magic of all teams working on a project, using integration and automation. 
With these ingredients, you get a cross-integration across all departments, QA+sysadmins+developers. 

For example, 
ensuring developers can now be involved in deployment and sysadmins can now write scripts, QA can figure out how to 
fix flaws vs constantly testing for functionality. By introducing automation and integration of systems, these 
engineers can now have the same visibility at all times and interact accordingly. We will dive more into how DevOps 
does this in the latter rooms as we talk about pipelines, automation, Continuous Integration and Continuous Delivery 
(CI/CD).

DevOps builds a philosophy that emphasises building trust and better liaising between developers and other teams 
(sysadmins, QA, etc.). This helps the organisation align technological projects to business requirements, increasing 
the impact and value to the business as projects become more efficient and prioritised accordingly. Changes rolled 
out are usually small and reversible, visible to all teams involved. This ensures better contribution and communication 
that helps with the pace and an increased competency when delivering work.

## TL;DR

Thanks to the advent of DevOps, today's development infrastructure is fully automated and operates on a self-service 
basis:

* Developers can provide resources to public clouds without depending on IT to provision infrastructure, which in the past led to weeks to months of delays.
* Continuous integration and deployment (CI/CD) processes automatically set up testing, staging, and production environments in the cloud or on-premises. They can be decommissioned, scaled, or re-configured as needed.
* Infrastructure-as-Code (IaC) is widely used to deploy environments declaratively*, using tools like Terraform and Vagrant.
* Organisations can now provision containerised workloads dynamically using automated, adaptive processes

*The declarative approach requires that users specify the end state of the infrastructure - for example, deploy these 
machines in a running state directly into an environment, automating the configuration choices throughout the workflow. 
The software builds it and releases it with no human interaction.

The imperative/procedural approach takes action to configure systems in a series of actionable steps. For example, 
you might declare to deploy a new version of the software and automate a series of steps to get a deployment-ready 
state. You choose when to apply those changes at the end by adding a "gate" this gate could be a button to release 
the changes, e.g. "deploy changes" button, after all the automated checks and new configurations pass.

In such a workflow, even a tiny problem could create a mess. Moreover, as the number of new releases increases 
(the actual case), the whole matter may turn disastrous. Things would surely go out of hand with an issue still 
unresolved and plenty of features scheduled to be released.

## Resources

* [History of DevOps](https://www.appknox.com/blog/history-of-devops)