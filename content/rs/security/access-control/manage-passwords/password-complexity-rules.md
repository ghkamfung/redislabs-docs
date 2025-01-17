---
Title: Enable password complexity rules
linkTitle: Password complexity rules
description: Enable password complexity rules.
weight: 30
alwaysopen: false
toc: "true"
categories: ["RS"]
aliases: 
---

Redis Enterprise Software provides optional password complexity rules that meet common requirements.  When enabled, these rules require the password to have:

- At least 8 characters
- At least one uppercase character
- At least one lowercase character
- At least one number
- At least one special character 

These requirements reflect v6.2.12 and later. Earlier versions did not support numbers or special characters as the first or the last character of a password. This restriction was removed in v6.2.12.

In addition, the password:

- Cannot contain the user's email address or the reverse of the email address.
- Cannot have more than three repeating characters.

Password complexity rules apply when a new user account is created and when the password is changed.  Password complexity rules are not applied to accounts authenticated by an external identity provider.  

You can use the admin console or the REST API to enable password complexity rules.

## Enable using the admin console

To enable password complexity rules using the admin console:

1. Sign in to the Redis Enterprise Software admin console using an administrator account

1. From the main menu, select **Settings** | **Preferences**

    {{<image filename="images/rs/cluster-settings-preferences.png" alt="Preference settings in the Redis Software admin console." width="75%">}}{{< /image >}}

1. Place a checkmark next to **Enable password complexity rules**

1. Save your changes

## Enable using the REST API

To use the REST API to enable password complexity rules:

``` REST
PUT https://[host][:port]/v1/cluster
{"password_complexity":true}
```

## Deactivate password complexity rules

To deactivate password complexity rules:

- Remove the checkmark from the **Enable password complexity rules** setting in the admin console

- Use the `cluster` REST API endpoint to set `password_complexity` to `false`
