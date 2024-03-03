## What's AWS CodeCommit?

AWS CodeCommit is a fully-managed source control service that host your secure Git-based repository. It make it easy for group to collaborate in code in a source and highly scalable ecosystem. CodeCommit eliminate the need to operate the source control on your own infrastructure. 


## Apply IAM policies


If you're familiar with IAM, then you understand the rules that can be established to govern access to AWS service. For intance, consider a scenario where you want to ensure that only a specific IP address has access to CodeCommit. By leveraging, IAM Policies in conjunction with CodeCommit, you can make this a reality



Exemple of policy whih that behavior
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "codecommit:GitPush",
            "Resource": "*",
            "Condition": {
                "IpAddress": {
                    "aws:SourceIp": "177.52.25.85"
                }
            }
        },
        {
            "Effect": "Allow",
            "Action": [
                "codecommit:*"
            ],
            "Resource": "*",
            "Condition": {
                "StringNotEquals": {
                    "codecommit:GitPush": "true"
                }
            }
        }
    ]
}


```




