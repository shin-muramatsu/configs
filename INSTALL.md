# A3 のインストール手順

## A3 インストール前の準備
### EPEL リポジトリの登録
```
# yum -y install epel-release
```

### SOCI ライブラリのインストール
```
yum -y install soci
```

## A3 モジュールのインストール
```
# yum -y install a3-1.0.0-rc1.el6.x86_64.rpm
```

## OpenLDAP の設定方法
### インストール
```
# yum -y install openldap-servers openldap-clients
```

### LDAP 用 DB の準備
```
# cp /usr/share/openldap-servers/DB_CONFIG.example /var/lib/ldap/DB_CONFIG
# chown ldap. /var/lib/ldap/DB_CONFIG
```

### slapd の起動
```
# chkconfig slapd on
# service slapd start
```

### 管理者パスワードの設定
```
# slappasswd
# vi rootpw.ldif [一時ファイル]
```
```
[rootpw.ldif]
dn: olcDatabase={0}config,cn=config
changetype: modify
add: olcRootPW
olcRootPW: <your hashed password>
```
