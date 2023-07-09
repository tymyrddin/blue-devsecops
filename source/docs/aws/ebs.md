# Elastic Block Store (EBS)

Amazon Elastic Block Store (Amazon EBS) is the AWS block storage. When working with EC2 instances, it is common practices to attach an additional volume to store data (separately from the operating system volume). 

Amazon EBS can be attached to a single EC2 instance and can be accessed from within the operating system. The traffic between the EC2 instance and the attached EBS volume is encrypted at transit (and is automatically configured and controlled by AWS). And, an EBS volume can be configured to encrypt data at rest for the rare scenario in which a potential attacker gains access to your EBS volume and wishes to access your data. The data itself (on the EBS volume and its snapshots) is only accessible by the EC2 instance that is connected to the EBS volume.

To create an encrypted EBS volume in a specific AWS availability zone:

```text
aws ec2 create-volume \
    --size 80 \
    --encrypted \
    --availability-zone <AWS_AZ_code>
```

To enable EBS encryption by default in a specific AWS region:

    aws ec2 enable-ebs-encryption-by-default --region <Region_Code>

## Best practices

* Configure encryption by default for each region you are planning to deploy EC2 instances. 
* Encrypt both boot and data volumes. 
* Encrypt each EBS volume at creation time. 
* Encrypt EBS volume snapshots. 
* Use AWS Config to detect unattached EBS volumes. 
* Use an IAM policy to define who can attach, detach, or create a snapshot for EBS volumes to minimize the risk of data exfiltration. 
* Avoid configuring public access to your EBS volume snapshots – make sure all snapshots are encrypted. 
* For highly sensitive environments, encrypt EBS volumes using the customer master key. 
* Set names and descriptions for EBS volumes to better understand which EBS volume belongs to which EC2 instance. 
* Use tagging (labelling) for EBS volumes to allow a better understanding of which EBS volume belongs to which EC2 instance.
