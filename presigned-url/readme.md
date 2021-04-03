**Simple Create presigned url for s3 object**

```
[root@ip-172-31-0-59 ~]# aws s3 presign s3://utils-kiwony/bash-5.0.tar.gz --expires-in 60
https://utils-kiwony.s3.ap-northeast-2.amazonaws.com/bash-5.0.tar.gz?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=ASIAZVQXJIKFITIW25YM%2F20210403%2Fap-northeast-2%2Fs3%2Faws4_request&X-Amz-Date=20210403T144249Z&X-Amz-Expires=60&X-Amz-SignedHeaders=host&X-Amz-Security-Token=IQoJb3JpZ2luX2VjEI7%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaDmFwLW5vcnRoZWFzdC0yIkYwRAIgUGOxGq5h2ZWVX7E7zN%2Fht3I%2BO7gjNJmXNiKbGIb56HwCIAVSi7D7SzgjBpY%2FQKnltO2j5CyMhePYcFQDyfesqXO1KscDCNf%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEQAhoMNjY0Njk1MDMwNDEwIgy%2BfeMylhId93ERNeQqmwOYfDDGlA0TvntMvWfxR0n6jhBq%2FlKS9mvd1NncOEt5Kwz8ysZW%2BERVevvccC%2BLr291fHkKqdTtB2bpQfa7hf7SUBd6qwoiYE29tC0A%2BcMRt83sEbCaYFm78gHCrhenKFd5ZPpnS7gjdXZnK5eA7xiTcFrCxzO1QQsGKU1TKd69Qof9a%2FxXAcO%2Fizdk17Xse5fY%2Bvs%2BbPW7oYM0lkW0q9fK4N8WZDmgqtIJDBGzvUWpFbiJb2MeDmHTBJbnps0DhJArxAHAHnOwfNLjUiYBPBiIkEmqPD5Jd9G9gpoAt3zeorXDpFPKoPBMCEAFJ897nS%2FfFNlNtEfuxGQCTMH4lNwieN7qUuU3MLE%2BFqXlRdw0gi8toq1eUcB0SvBYGfFWGsOSQnQg%2BFynLn%2Fl7MkHAxevaM%2Fb6HbpW%2BXKcuwY4kaql%2B3OoAt68JZT9wp8ylH7TZH6N3s26Qum2Nd1xIczrurExAf6XGVkMvRfIB1kH79Y0Yr6RpIznVGTueJ0uOhcUzbKORDdgmWJIDqeerbl5a3qsQXRsWHezty7f7owoeuhgwY67AGR7aJCQWYK2Efl4Krfqy065SjHcsoZSvzBKPmgtGYdR9%2F%2BiZHL2AZhLMNiV7MqVF2BSKqN8hX980MRDRrtJ2UJIAUEcelujl9KfNHskLYpq19WWjN8KQHuWFXCjDX3H1QNgtYvphyAefOpgBjeK6uJucSK3xEa8AccJOhUgEv6Q46%2BsHPwQxJ%2B1W4meXXesNxDZJBcb8mlcNGC%2FVuBvPhISFznHGjqpB35wJyCjqeitIMC8lKWR54IxZUAEsITqTCGwRDP8fyI2xzrSGuzIQekoC4BSH%2FnjJkDukODr9j8bSYXZVglWHX6%2FcMl9A%3D%3D&X-Amz-Signature=3e5307e871b7a204fb54ea73d08c319d9ccf989ebc680b32af92220f8bb6ba80
```

**wget file from presigned url**

```
[root@ip-172-31-0-59 ~]# aws s3 presign s3://utils-kiwony/bash-5.0.tar.gz --expires-in 60 | xargs wget -O bash-5.0.tar.gz "$1"
Downloaded: 1 files, 9.7M in 0.06s (152 MB/s)
[root@ip-172-31-0-59 ~]# ls bash*.tar.gz
bash-5.0.tar.gz
```

**wget with presigned url example**

```
mkdir -p /root/urls
aws s3 presign s3://utils-kiwony/bash-5.0.tar.gz --expires-in 600 > /root/urls/bash-url.txt
cd /usr/local/src/
cat /root/urls/bash-url.txt |xargs wget -O bash-5.0.tar.gz
tar zxvf bash-5.0.tar.gz
```
