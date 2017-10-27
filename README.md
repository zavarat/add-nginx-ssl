# add-nginx-ssl

Add SSL config to nginx

```
npm install -g add-nginx-ssl
```

## Usage

``` shell
# setup ssl for example.com
add-nginx-ssl --key my-key.pem --cert my-cert.crt --dhparam my-dhparam.pem --domain example.com

# or if you have a wildcard ssl cert
add-nginx-ssl --key my-key.pem --cert my-cert.crt --dhparam my-dhparam.pem --domain *.example.com

# or to just only allow ssl
add-nginx-ssl --key my-key.pem --cert my-cert.crt --dhparam my-dhparam.pem --all
```

Running the above will write the SSL config to /etc/nginx/conf.d/ssl.conf and reload nginx.

Protip, to generate the dhparam.pem file you can use the following command

``` shell
openssl dhparam -outform pem -out dhparam2048.pem 2048
```

# Using Let's Encrypt

If you don't have a certificate but have certbot installed (the command line tool for [Let's Encrypt](https://letsencrypt.org/)), add-nginx-ssl can auto issue the certificates for you.

``` shell
# use let's encrypt
add-nginx-ssl --letsencrypt -d my-domain.com -d my-other-domain.com
```

## License

MIT
