**Create presigned url for s3 object**

```
kiwony@kiwonymac.com:/Users/kiwony/temp> aws s3 presign s3://utils-kiwony/bash-5.0.tar.gz --expires-in 60
https://utils-kiwony.s3.ap-northeast-2.amazonaws.com/bash-5.0.tar.gz?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAZVQXJIKFKYATZFC5%2F20210403%2Fap-northeast-2%2Fs3%2Faws4_request&X-Amz-Date=20210403T135803Z&X-Amz-Expires=60&X-Amz-SignedHeaders=host&X-Amz-Signature=d4a20669353126786672da8019a67bdb8f33df2cab99b9aacc1dca5bc38d93b4
```

**wget with presigned url example**

```
mkdir -p /root/urls
aws s3 presign s3://utils-kiwony/bash-5.0.tar.gz --expires-in 600 > /root/urls/bash-url.txt
cd /usr/local/src/
cat /root/urls/bash-url.txt |xargs wget -O bash-5.0.tar.gz
tar zxvf bash-5.0.tar.gz
```
