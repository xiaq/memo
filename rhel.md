List package files: `rpm -ql [package-name]`

Find file supplier: `rpm -qf [/full/path/to/file]`

# Configure nslcd

1. yum install openldap-devel krb5-devel nss-devel pam-devel

2. install nss-pam-ldap aka nslcd nss-ldapd

3. generate nslcd.conf

4. chmod o= /etc/nslcd.conf

5. add user nslcd

6. authconfig-tui

7. start nslcd and add nslcd to rc.local
