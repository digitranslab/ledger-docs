---
sidebar_position: 3
---

# Signup Restriction

This document describes ways to restrict users from signing up on your self-hosted Ledger instance. This configuration is done by editing envirement variables of the instance.

## Disable Signup

The environment variable `SIGNUP_DISABLED` should be set to `true` to disable the signing up of new users. When set, the following facts hold:

- The **Register link** in Login page will disappear but you can access to the page directly through `/auth/register` url and the page will show up but when sign-up the form will throw an error.
- **Uninvited users** cannot sign-up using the signup form.
- **Invited users** can still signup using the signup form.

:::tip

This environment variable's value does not affect the login behavior of existing users.

:::

```
SIGNUP_DISABLED=true
```

## Email domains white-list

The environment variable `SIGNUP_ALLOWED_DOMAINS` can be used to restrict signups to emails belonging to only a specific set of domains. This field takes a comma-separated set of values.

Setting `SIGNUP_ALLOWED_DOMAINS`=ledger.ly allows developers@digi-trans.org to sign up, but not ahmed@gmail.com.

:::info

You should set `SIGNUP_DISABLED` to `true` first to allow a specific set of domains.

:::

```
SIGNUP_DISABLED=true
SIGNUP_ALLOWED_DOMAINS=ledger.io,self-hosted.com
```

## Email addresses white-list

The environment variable `SIGNUP_ALLOWED_EMAILS` can be set to a comma-separated list of email addresses, that is always allowed to sign up, irrespective of the above environment variable.

:::info

You should set `SIGNUP_DISABLED` to `true` first to allow a specific set of email addresses.

:::

```
SIGNUP_DISABLED=true
SIGNUP_ALLOWED_EMAILS=developers@digi-trans.org,hello@gmail.com
```

These two email addresses can sign up on the Ledger instance.
