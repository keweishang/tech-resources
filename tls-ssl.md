# Use OpenSSL to generate an auto-signed certificate

1. `openssl genrsa -des3 -out server.key 2048`

The first command will generate a 2048 bit(recommended) RSA private key . After running the command it will ask for the passphrase. If you want to create a key without the passphrase you can remove the (-des3) from the command.

2. `openssl req -new -key server.key -out server.csr`

The second command generates a CSR(Certificate Signing Request).  The CA will use the .csr file and issue the certificate, but in your case you can use this .csr file to create your self-signed certificate. Once you run the command, it will prompt you to enter your country, company name, etc.
If you want to configure your certificate for localhost you can give ‘localhost’ in Common Name field instead of  domain name.

3. `openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt`

The third command will create the self-signed x509 certificate suitable for use on web server.

## Transform certificate to pem and pkcs12 format (optional)

1. `cat server.key > server.pem`
2. `cat server.crt >> server.pem`

A **.pem(Privacy Enhanced Mail)** file is a container format that may just include the public certificate or the entire certificate chain (private key, public key, root certificates).

The existing key and the certificate would be there in your server.pem file. The Structure of .pem file looks like this:
```
—–BEGIN RSA PRIVATE KEY—–
(Private Key: domain_name.key contents)
—–END RSA PRIVATE KEY—–
—–BEGIN CERTIFICATE—–
(Primary SSL certificate: domain_name.crt contents)
—–END CERTIFICATE—–
```

3. `openssl pkcs12 -export -in server.pem -out keystore.pkcs12`

This command will generate the KeyStore with name keystore.pkcs12, you can use the KeyStore for configuring you server.

# Use JDK's keytool to generate an auto-signed certificate
`keytool -genkey -keyalg RSA -alias tomcat -keystore selfsigned.jks -validity <days> -keysize 2048`
- Enter a password for the keystore
- When prompted for a first name and the last name, enter the domain name of the server. For example, myserver or myserver.mycompany.com
- When prompted with "Enter key" password for <tomcat>, press Enter to use the same password as the keystore password
- Run this command to verify the contents of the keystore. `keytool -list -v -keystore selfsigned.jks`
- When prompted, enter the keystore password.

# Use OpenSSL to check certificate information

## Check a certificate in pem format
`openssl x509 -in server.pem -text`

## Check a certificate in crt format
`openssl x509 -in server.crt -text`

## Check a certificate in pkcs12 format (.pfx or .p12 or .pkcs12)
`openssl pkcs12 -info -in keyStore.p12`

# Use Java's keytool to check certificate information

## Check a certificate in pem format
`keytool -printcert -file server.pem`

## Check a certificate (in a keystore) in jks format
`keytool -list -v -keystore selfsigned.jks` (When prompted, enter the keystore password)
