# ✈️DecryptExample
针对 Jasypt druid解密，同时可以针对密钥进行进行爆破。
```
root@ubuntu:/tmp# java -jar DecryptExample-1.0-SNAPSHOT.jar 
DecryptExample by RuoJi v1.0
使用说明：
java -jar DecryptExample.jar <命令> <加密数据> <密钥 | 密钥文件>

命令：
  jasypt <加密数据> <密钥 | 密钥文件>     使用 Jasypt 解密数据
  druid1.0.16 <加密数据>    使用 Druid 1.0.16 以前版本 解密数据
  druid <加密数据> <密钥 | 密钥文件>      使用 Druid 1.1.16 及以后版本解密数据

帮助：
  --help 或 -h 显示此帮助信息
```
## 🚀优点
1、支持`Jasypt`加密算法：`MD5，SHA1，SHA256，SHA512，SHA512`等，21个常见加密算法进行解密，自动爆破可利用算法。

2、支持`druid1.0.16以`前版本解密，以及以后版本解密。

3、支持`Jasypt`和`druid`自定义密码字典爆破解密。

```
root@ubuntu:/tmp# java -jar DecryptExample-1.0-SNAPSHOT.jar jasypt stqvirrvG8TcLz9mqflBDQ== EbfYkitulv73I2p0mXI50JMXoaxZTKJ7
[+]-----jasypt-----[+]
[+]key: EbfYkitulv73I2p0mXI50JMXoaxZTKJ7
[+]pass: stqvirrvG8TcLz9mqflBDQ==
[+]------------------------->  解密算法: PBEWithMD5AndDES 成功: 123456
解密结果: 123456
root@ubuntu:/tmp# java -jar DecryptExample-1.0-SNAPSHOT.jar druid1.0.16 hbZoFfr14R2yGuWJwbUtYdXjF40Df5sXbHSJYzGECsK0p1W4bmrM64SJKU0rmWo+yjUSrtU1Drb+0eGhQT3Xlg==
[+]-----druid1.0.16以前版本-----[+]
[+]pass: hbZoFfr14R2yGuWJwbUtYdXjF40Df5sXbHSJYzGECsK0p1W4bmrM64SJKU0rmWo+yjUSrtU1Drb+0eGhQT3Xlg==
[+]-------------------------> 成功: hhpt
解密结果: hhpt
root@ubuntu:/tmp# java -jar DecryptExample-1.0-SNAPSHOT.jar druid Obsbr4gd1oVyYr+k4KQdUMNYgKMWdDibsNJTabnph+yPmxjc6tUrT1GNsPDqa9ZvTF9QvaRD86H+Zn/H+yz2jA== MFwwDQYJKoZIhvcNAQEBBQADSwAwSAJBAKHGwq7q2RmwuRgKxBypQHw0mYu4BQZ3eMsTrdK8E6igRcxsobUC7uT0SoxIjl1WveWniCASejoQtn/BY6hVKWsCAwEAAQ==
[+]-----druid-----[+]
[+]key: MFwwDQYJKoZIhvcNAQEBBQADSwAwSAJBAKHGwq7q2RmwuRgKxBypQHw0mYu4BQZ3eMsTrdK8E6igRcxsobUC7uT0SoxIjl1WveWniCASejoQtn/BY6hVKWsCAwEAAQ==
[+]pass: Obsbr4gd1oVyYr+k4KQdUMNYgKMWdDibsNJTabnph+yPmxjc6tUrT1GNsPDqa9ZvTF9QvaRD86H+Zn/H+yz2jA==
[+]-------------------------> 成功: wusc.321
解密结果: wusc.321
root@ubuntu:/tmp# java -jar DecryptExample-1.0-SNAPSHOT.jar jasypt stqvirrvG8TcLz9mqflBDQ== passkey.txt 
[+]-----jasypt-----[+]
[+]尝试使用密钥: admin
[+]尝试使用密钥: 1234567
[+]尝试使用密钥: EbfYkitulv73I2p0mXI50JMXoaxZTKJ7
[+]key: EbfYkitulv73I2p0mXI50JMXoaxZTKJ7
[+]pass: stqvirrvG8TcLz9mqflBDQ==
[+]------------------------->  解密算法: PBEWithMD5AndDES 成功: 123456
解密结果: 123456
root@ubuntu:/tmp# java -jar DecryptExample-1.0-SNAPSHOT.jar druid Obsbr4gd1oVyYr+k4KQdUMNYgKMWdDibsNJTabnph+yPmxjc6tUrT1GNsPDqa9ZvTF9QvaRD86H+Zn/H+yz2jA== passkey.txt 
[+]-----druid-----[+]
[-]使用密钥 admin 解密失败: Failed to get public key
[-]使用密钥 1234567 解密失败: Failed to get public key
[-]使用密钥 EbfYkitulv73I2p0mXI50JMXoaxZTKJ7 解密失败: Failed to get public key
[+]key: MFwwDQYJKoZIhvcNAQEBBQADSwAwSAJBAKHGwq7q2RmwuRgKxBypQHw0mYu4BQZ3eMsTrdK8E6igRcxsobUC7uT0SoxIjl1WveWniCASejoQtn/BY6hVKWsCAwEAAQ==
[+]pass: Obsbr4gd1oVyYr+k4KQdUMNYgKMWdDibsNJTabnph+yPmxjc6tUrT1GNsPDqa9ZvTF9QvaRD86H+Zn/H+yz2jA==
[+]-------------------------> 成功: wusc.321
解密结果: wusc.321
root@ubuntu:/tmp# 
```
![image](https://github.com/user-attachments/assets/39ce54fc-e9c8-4e49-91ec-f126beda4331)
