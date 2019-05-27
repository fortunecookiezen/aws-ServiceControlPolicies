# aws-ServiceControlPolicies
a repository of aws Organizations Service Control Policies

AWS Organizations is an account management service that enables you to consolidate multiple AWS accounts into an organization that you create and centrally manage. This repository contains [Service Control Policies](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scp.html) that define member account behavior.

## SCP Strategy

The examples here are examples of implementing _blacklisting_. The default configuration of AWS Organizations supports using SCPs as blacklists. Using a blacklist strategy, account administrators can delegate all services and actions until you create and attach an SCP that denies (blacklists) a specific service or set of actions. Using deny statements in SCPs require less maintenance, because you don't need to update them when AWS adds new services.

For a more restrictive set of policies, use _whitelisting_ instead. The maximum size of a service control policy (SCP) document is 5,120 bytes. This includes all characters, including white space. Whitelisting is most useful for regulatory compliance, such as HIPAA.

## MemberAccountPolicy.json

This policy is the consolidated policy of all of the feature policies that can be applied to an Organization Unit or individual Accounts.

It implements the following:

1. Sid: "RegionEnforcement" restricts member accounts to specific regions. This is required if compliance is an issue, however it's also useful to prevent resources from appearing all over the place.
2. Sid: "RoleProtection" protects administrative roles in member accounts. If you have administrative roles in member accounts, this prevents those roles from being deleted by account administrators.
3. Sid: "DenyDomainRegistration" prevents member accounts from registering domain names. In theory, you want to centralize this.
4. Sid: "DenyReservedInstancePurchase" denies the listing, purchasing, and trading of reserved instances. This can be optimized at the organization master level.
5. Sid: "PreventVpcPeering" prevents vpc peering. If you have a member account policy that prohibits east-west network traffic, this can be used to enforce that.

### References

https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scp.html
https://docs.aws.amazon.com/organizations/latest/userguide/SCP_strategies.html
https://docs.aws.amazon.com/general/latest/gr/rande-manage.html
https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_example-scps.html
