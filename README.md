# CS4.0-Malleable-c2-profile


使用letsencrypt 生成 C2 profile


（1）lets encrypt 生成PKCS12 Keystore:

```openssl pkcs12 -export -in fullchain.pem -inkey privkey.pem -out demopic2.pkcs -name api.demopic2.ga -passout ggbond```


（2）生成java keystore

```keytool -importkeystore -deststorepass ggbond  -destkeypass ggbond -destkeystore demopic2.store -srckeystore demopic2.pkcs -srcstoretype PKCS12 -srcstorepass ggbond -alias api.demopic2.ga```

(3) c2 profile:

 ```https-certificate {
    set keystore "demopic2.store";
    set password "ggbond";
}
```
