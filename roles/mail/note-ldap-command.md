/usr/sbin/slappasswd -h {SSHA} >> ~/newpasswd.ldif


sudo wget -O postfix.ldif https://raw.githubusercontent.com/68b32/postfix-ldap-schema/master/postfix.ldif
sudo ldapadd -Q -Y EXTERNAL -H ldapi:/// -f ../postfix.ldif

sudo ldapadd -x -w y7pcASQ7T77S -D cn=admin,dc=tsec901g3,dc=tk -H ldap://ldap.tsec901g3.tk -f postfix-Mail-user.ldif
""""
dn: ou=Mail,dc=example,dc=com
objectclass: organizationalUnit
objectclass: top
ou: Mail
""""

sudo ldapadd -x -w y7pcASQ7T77S -D cn=admin,dc=tsec901g3,dc=tk -H ldap://ldap.tsec901g3.tk -f postfix-user.ldif
""""
dn: uid=mail000,ou=Mail,dc=example,dc=com
cn: mail000
gidnumber: 20000
homedirectory: /home/mail/mail000
mailacceptinggeneralid: test0@hosted-domain.com
mailacceptinggeneralid: test1@hosted-domain.com
maildrop: mail000@mail.example.com
objectclass: account
objectclass: posixAccount
objectclass: postfixUser
objectclass: top
uid: mail000
uidnumber: 20000
#password
userpassword: {SSHA}ncdXGXXD6zaG76dSCVKVAQLH4vPcHaTa
""""
