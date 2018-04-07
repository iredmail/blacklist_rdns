# Kill spammers based on client reverse hostname

File `blacklist_rdns.pcre` is PCRE rules used to match client reverse hostname
and reject matched client.

It's based on file `fqrdns.pcre` from <https://github.com/stevejenkins/hardwarefreak.com-fqrdns.pcre>.

This file is provided AS IS with no WARRANTY. It is free software, without
attribute or copyright, and without license. As such, you are completely free
to use it and modify it as you see fit, for your purposes, with absolutely no
strings attached.

# Usage

* Download the `blacklist_rdns.pcre` in `/etc/postfix/`.
* Update `smtpd_client_restrictions =` in `/etc/postfix/main.cf`, include this
  file like below:

```
smtpd_client_restrictions =
    ...
    permit_sasl_authenticated
    check_client_access pcre:/etc/postfix/blacklist_rdns.pcre
    ...
```

Make sure the `check_client_access` rule is after `permit_sasl_authenticated`.

# Additional Patterns

If you would like to propose a pattern which isn't currently covered, please
create a new issue or pull request on <https://github.com/iredmail/blacklist_rdns.pcre>
so it can be considered for inclusion in the appropriate list.
