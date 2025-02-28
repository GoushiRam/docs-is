# Administration of sub organizations

The following guides explain how to manage the administration tasks of sub organizations.

## Implement an administration portal

Sub organization administrators do not have access to the {{ product_name }} Console. Therefore, you should expose administrative functions to administrators through a separate administration portal in your application.

The administration portal of your application should use [{{ product_name }}'s sub organization APIs]({{base_path}}/apis/organization-management/) to perform administrative operations.

!!! note
    To access management APIs in {{ product_name }}, you need to register your application as a management application. Learn how to [register a management application]({{base_path}}/apis/authentication/#register-a-management-app) in {{ product_name }}.

The following are some of the features that your administration portal should contain.

### Manage users

The sub organization administrator should be able to onboard new users (administrators and consumers) to the sub organization. The identities of these users are stored in the default {{ product_name }} user store.

The identity and access management requirements of these users will be managed by {{ product_name }}.

The administration portal in your application should use the [User management - SCIM2 API]({{base_path}}/apis/organization-management/org-scim2/#/) to create user operations.

### Onboard identity providers

A sub organization may have an external identity provider (IdP) to manage the user identities of its employees and customers. Such an IdP may be already being used for the following purposes:

- Authenticating user logins to various applications.
- Branding the login interfaces to suit the organization.
- Enabling custom login experiences to different user groups.

The sub organization administrator can onboard such corporate IdPs to the sub organization in {{ product_name }} as a connection. These IdPs can then be set as a login option in your application.

The administration portal in your application should use the [identity provider API]({{base_path}}/apis/organization-management/org-idp/#/) to manage external IdPs.

### Define application login flows

Sub organization administrators should be able to customize the login flows of the application to suit business needs.

For example, the administrator should be able to define the number of authentication steps that the application login flow needs and what login options should be available for each step.

The administration portal in your application should use the [application management API]({{base_path}}/apis/organization-management/org-application-management/#/) to manage application login flows.

### Extend administration tasks

Explore the [sub organization APIs]({{base_path}}/apis/organization-management/) of {{ product_name }} that are available for you to enable all the required administration capabilities from your administration portal.

!!! note
    See the instructions on [enabling organization login]({{base_path}}/guides/authentication/add-organization-login/) to try out a B2B organization login use case.
