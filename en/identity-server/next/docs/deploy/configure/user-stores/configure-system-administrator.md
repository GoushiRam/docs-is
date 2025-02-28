# Configure the System Administrator

This documentation explains the main settings relevant to the system
administrator.

The **admin** user manages all
other users, roles, and permissions in the system. Therefore, the user that should have admin
permissions is required to be stored in the primary user store when you
start the system for the first time. The documentation on setting up
primary user stores will explain how to configure the administrator
while configuring the user store. The information under this topic will
explain the main configurations that are relevant to setting up the
system administrator.

!!! note
    If the primary user store is read-only, you will be using a user ID and
    role that already exists in the user store, for the administrator. If
    the user store is read/write, you have the option of creating the
    administrator user in the user store as explained below. By default, the
    embedded H2 database (with read/write enabled) is used for both these
    purposes in WSO2 products.
    

Note the following key facts about the system administrator in your
system.

-   The admin user and role are always stored in the primary user store
    in your system.
-   An administrator is configured for your system by default. This
    **admin** user is assigned to the **admin** role, which has all
    permissions enabled.
-   The permissions assigned to the default **admin** role cannot be
    modified.

---

## Before you begin

Ensure that you have a primary user store (for storing users and roles)
and an RDBMS (for storing information related to permissions).

---

## Update the administrator

The `<IS_HOME>/repository/conf/deployment.toml` file allows you to configure the administrator user in your system as well as
the RDBMS that will be used for storing information related to user
authentication (i.e. role-based permissions).

``` toml
[super_admin]
create_admin_account= true
admin_role = "admin"
username = "admin"
password = "admin"
create_admin_account= true
```

Note the following regarding the configuration above.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><code>              create_admin_account             </code></td>
<td>When <code>              true             </code>, this element creates the admin user based on the <code>              AdminUser             </code> element. It also indicates whether to create the specified admin user if it doesn't already exist. When connecting to an external read-only LDAP or Active Directory user store, this property needs to be <code>              false             </code> if an admin user and admin role exist within the user store. If the admin user and admin role do not exist in the user store, this value should be <code>true</code>, so that the role is added to the user management database. However, if the admin user is not there in the user store, we must add that user to the user store manually. If the <code>              create_admin_account             </code> value is set to <code>              true             </code> in this case, it will generate an exception.</td>
</tr>
<tr class="even">
<td><code>              admin_role = "wso2admin"            </code></td>
<td>This is the role that has all administrative privileges of the WSO2 product, so all users having this role are admins of the product. You can provide any meaningful name for this role. This role is created in the internal H2 database when the product starts. This role has permission to carry out any actions related to the Console. If the user store is read-only, this role is added to the system as a special internal role where users are from an external user store.</td>
</tr>
<tr class="even">
<td><code>              username          </code></td>
<td>This is the username of the default administrator of the user store. If the user store is read-only, the admin user MUST exist in the user store for the process to work.</td>
</tr>
<tr class="odd">
<td><code>              password             </code></td>
<td><p>Do NOT put the password here but leave the default value. If the user store is read-only, this element and its value are ignored. This password is used only if the user store is read-write and the <code>            create_admin_account           </code> value is set to <code>               true              </code>.</p>
<div class="admonition note">
<p class="admonition-title">Note</p>
    <p>Note that the password in the <code>deployment.toml</code> file is written to the primary user store when the server starts for the first time. Thereafter, the password will be validated from the primary user store and not from the <code>deployment.toml</code> file. Therefore, if you need to change the admin password stored in the user store, you cannot simply change the value in the <code>deployment.toml</code> file. To change the admin password, you must use the <strong>Change Password</strong> option from the management console. See the <a href="{{base_path}}/guides/identity-lifecycles/manage-user-overview/">changing a password</a> for instructions.
    </p></div></td>
</tr>
</tbody>
</table>
