# CS4.0-Malleable-c2-profile

在certbot 目录执行： ./certbot-auto renew 更新证书

使用letencrypt生成的证书文件有多个，只使用fullchain.pem 和 privkey.pem生成keystore文件

使用letsencrypt 生成 C2 profile


（1）lets encrypt 生成PKCS12 Keystore:

```openssl pkcs12 -export -in fullchain.pem -inkey privkey.pem -out demopic2.pkcs -name api.demopic2.ga -passout pass:ggbond```


（2）生成java keystore

```keytool -importkeystore -deststorepass ggbond  -destkeypass ggbond -destkeystore demopic2.store -srckeystore demopic2.pkcs -srcstoretype PKCS12 -srcstorepass ggbond -alias api.demopic2.ga```

(3) c2 profile:

 ```
 https-certificate {
    set keystore "demopic2.store";
    set password "ggbond";
}
```
