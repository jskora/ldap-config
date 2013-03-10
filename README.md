# ldap-config

Setup LDAP server on Ubuntu (12.10)

* based on [https://help.ubuntu.com/12.10/serverguide/openldap-server.html]

## Notes/Variations from document:

* DIT = Domain Information Tree
_add_content.ldif_ was split into add_organizationUnits.ldif, add_group.ldif, add_user.ldif.

* change a user's LDAP password with:
> ldappasswd -x -W -D cn=admin,dc=localdomain -S "uid=<user>,ou=people,dc=localdomain"

* useful configuration information not covered above including setting passwords and 
setting PAM modules (http://techpubs.spinlocksolutions.com/dklar/ldap.html)

* resolved permission errors during Initialise Database
(https://github.com/gitlabhq/gitlabhq/issues/1799)

:::bash
     $ sudo usermod -a -G git gitlab
     $ sudo usermod -a -G gitlab git

* to proxy through apache, add these lines to /etc/apache2/conf.d/gitlab.conf
> ProxyPass /gitlab http://tuttle.localdomain:8088/gitlab
> ProxyPassReverse /gitlab http://tuttle.localdomain:8088/gitlab



## other references:
> (http://qdelance.drupalgardens.com/content/building-ldap-directory-using-openldap-debian-squeeze)
> (http://wiki.debian.org/LDAP/OpenLDAPSetup)
> (http://www.debian-administration.org/article/OpenLDAP_installation_on_Debian)

