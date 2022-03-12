---
layout: post
title: 微信小程序获取海外手机号go语言代码
description: 微信小程序获取海外手机号go语言代码
category: 007-go
---


##### 微信小程序 开放数据校验与解密描述
```
加密数据解密算法
接口如果涉及敏感数据（如wx.getUserInfo当中的 openId 和 unionId），接口的明文内容将不包含这些敏感数据。开发者如需要获取敏感数据，需要对接口返回的加密数据(encryptedData) 进行对称解密。 解密算法如下：
对称解密使用的算法为 AES-128-CBC，数据采用PKCS#7填充。
对称解密的目标密文为 Base64_Decode(encryptedData)。
对称解密秘钥 aeskey = Base64_Decode(session_key), aeskey 是16字节。
对称解密算法初始向量 为Base64_Decode(iv)，其中iv由数据接口返回。
微信官方提供了多种编程语言的示例代码（（点击下载）。每种语言类型的接口名字均一致。调用方式可以参照示例。
另外，为了应用能校验数据的有效性，会在敏感数据加上数据水印( watermark )
```



##### 问题

    由于微信小程序官方没有go解密代码示例程序；

    在参考了某些代码以后，在解密国内手机号是没有问题，但解密海外手机号时报如下错误：
    
    invalid character '\x0f' after top-level value
    
    分析原因是在去除填充的时候遇到了问题；

##### 解决方案
```go
// 正确代码如下
func decryptData(appid, sessionKey, encryptData, iv string) (map[string]interface{}, error) {
   decodeBytes, err := base64.StdEncoding.DecodeString(encryptData)
   if err != nil {
      return nil, err
   }
   sessionKeyBytes, err := base64.StdEncoding.DecodeString(sessionKey)
   if err != nil {
      return nil, err
   }
   ivBytes, err := base64.StdEncoding.DecodeString(iv)
   if err != nil {
      return nil, err
   }
   dataBytes, err := aesDecrypt(decodeBytes, sessionKeyBytes, ivBytes)

   m := make(map[string]interface{})
   err = json.Unmarshal(dataBytes, &m)
   if err != nil {
      return nil, err
   }
   temp := m["watermark"].(map[string]interface{})
   rsAppid := temp["appid"].(string)
   if rsAppid != appid {
      logging.Info("invalid appid", temp["appid"])
      return nil, errors.New("invalid appid")
   }
   return m, nil
}

//{"phoneNumber":"1508272xxxx","purePhoneNumber":"1508272xxxx","countryCode":"86","watermark":{"timestamp":1539657521,"appid":"wx123456cccc"}}//<nil>
func aesDecrypt(crypted, key, iv []byte) ([]byte, error) {
   block, err := aes.NewCipher(key)
   if err != nil {
      return nil, err
   }

   blockMode := cipher.NewCBCDecrypter(block, iv)
   origData := make([]byte, len(crypted))
   blockMode.CryptBlocks(origData, crypted)

   length := len(origData)
   unp := int(origData[length-1])

   return origData[:(length - unp)], nil
}
```

##### 参考链接
- [微信小程序 开放数据校验与解密描述](https://developers.weixin.qq.com/miniprogram/dev/framework/open-ability/signature.html)
- [国内手机号ok](https://blog.csdn.net/qq_27507377/article/details/83784511)
- [国内外手机号都ok](https://blog.csdn.net/Douz_lungfish/article/details/118702489)
- [GO加密解密之DES](http://blog.studygolang.com/2013/01/go%E5%8A%A0%E5%AF%86%E8%A7%A3%E5%AF%86%E4%B9%8Bdes/)
- [三种填充模式的区别](https://www.jianshu.com/p/de84d355c96d)










