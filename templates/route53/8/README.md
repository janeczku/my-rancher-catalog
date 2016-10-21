## Route53 DNS

Rancher External DNS service powered by Amazon Route53

#### Upgrade Notes
If you are upgrading from a previous version don't change the TTL. Otherwise custom records might get deleted
during the upgrade process.
Note: Environment names using in service FQDNs are now sanitized to only include aZ. If your environment names
contain other characters this may cause your current service FQDNS to change.

State is tracked. Please do not delete the state record!
Rancher external-dns is now tracking the FQDN's it is managing in a TXT record external-dns-<environemntUUID>.domain.
Please do not delete this record.

#### Required AWS IAM permissions
The following IAM policy describes the minimum set of permissions needed for Route53 DNS to work.
Make sure that the AWS security credentials (Access Key ID / Secret Access Key) that you are providing in the template have been granted these permissions.

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "route53:GetHostedZone",
                "route53:GetHostedZoneCount",
                "route53:ListHostedZonesByName",
                "route53:ListResourceRecordSets"
            ],
            "Resource": [
                "*"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "route53:ChangeResourceRecordSets"
            ],
            "Resource": [
                "arn:aws:route53:::hostedzone/<HOSTED_ZONE_ID>"
            ]
        }
    ]
}
``` 

Note: When using this JSON document to create a custom IAM policy in AWS, replace `<HOSTED_ZONE_ID>` with the ID of the Route53 hosted zone or use a wildcard ('*').