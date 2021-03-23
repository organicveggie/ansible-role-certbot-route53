# Certbot Route53

Ansible Role for setting up wildcard certificates with Certbot and Route53.

## Requirements

* AWS Route53 domain setup
* AWS Access Key
* AWS Secret Access Key

## Role Variables

```
certbot_domain_name: example.com
```
The wildcard domain to create the certificate for. [Boto](https://github.com/boto/boto3) will automatically figure out the hosted zone id from the domain name and AWS credentials.

```
certbot_admin_email: email@example.com
```

Your email address, used by Let's Encrypt to send notifications.

```
certbot_aws_access_key_id: "ABCDEFGHIJKLMEXAMPLE"
certbot_aws_secret_access_key: "oRgAnICvEggIE/BROCCOL/iCeLeriACEXAMPLE12"
```

AWS access key and secret key. Populates  `/root/.aws/config`. Used to create the records in Route53 for the DNS challenge.

## Dependencies

* community.general collection

## Sample AWS IAM Policy

```json
{
    "Version": "2012-10-17",
    "Id": "certbot-dns-route53 sample policy",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "route53:ListHostedZones",
                "route53:GetChange"
            ],
            "Resource": [
                "*"
            ]
        },
        {
            "Effect" : "Allow",
            "Action" : [
                "route53:ChangeResourceRecordSets"
            ],
            "Resource" : [
                "arn:aws:route53:::hostedzone/YOURHOSTEDZONEID"
            ]
        }
    ]
}
```

## License

[Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0)

## See Also

* [michaelpporter/ansible-role-certbot-cloudflare](https://github.com/michaelpporter/ansible-role-certbot-cloudflare)
* [geerlingguy.certbot] (https://github.com/geerlingguy/ansible-role-certbot)
