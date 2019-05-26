# aws-ServiceControlPolicies
a repository of aws Organizations Service Control Policies

AWS Organizations is a service that does something blah blah blah. This repository contains Service Control Policies link to scp that define member account behavior.

## SCP Strategy

The examples here are examples of implementing _blacklisting_ for a more restrictive set of policies, use _whitelisting_ instead.

## MemberAccountPolicy.json

This policy is the consolidated policy of all of the feature policies that can be applied to an Organization Unit or individual Accounts.

It implements the following:

1) Restricts member accounts to specific regions. This is required if compliance is an issue, however it's useful to prevent resources from appearing all over the place
2) Protects Administrative Roles. If you have administrative roles in member accounts, this prevents those roles from being deleted by account administrators. 

### References

https://docs.aws.amazon.com/organizations/latest/userguide/SCP_strategies.html
https://docs.aws.amazon.com/general/latest/gr/rande-manage.html
https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_example-scps.html
