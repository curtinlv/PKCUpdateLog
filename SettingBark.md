PKC助手-Bark消息推送

+ 适用场景：多开证书无法后台推送消息通知；或推送到另一个设备上
+ wx需要常驻后台，通过Bark接收，Bark可以无后台

# ①推送API配置示例

1. 在Apple Store 下载 Bark App

   <img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/DownloadBark.png" alt="image-20230525224107878" style="zoom: 25%;" />

2. 打开Bark-服务器-右上角☁️-点击Bark官方api-复制地址和Key

   <img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/2.png" alt="image-20230525224156396" style="zoom: 25%;" />

   <img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/CopyApi.png" alt="image-20230525224213290" style="zoom: 25%;" />

3. 填写到PKC助手-推送API即可

   api正确的格式为(后面/不能删掉)：

   https://api.day.app/xxxxxxx/

   <img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/pkc-api.png" alt="image-20230525224344436" style="zoom: 25%;" />

   

   # ②PKC助手-Bark加密推送

   + “加密推送”配置后，能保证推送的消息不会被Bark服务器 和 苹果APNs截取或泄露。

   加密推送配置示例：

   a. 打开 Bark APP-服务器-滑动到“加密设置”，点击蓝色的 `加密配置`

   <img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/JiaMi.png" alt="image-20230525224904411" style="zoom: 25%;" />
   
   

b. 自己自定义一个Key和iv的值，规范要16位字母或数字混合都行，其他不用动，如下图：

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/setKeyAndIv.png" alt="image-20230525225009848" style="zoom: 25%;" />

c. 然后记住这Key和iv的值，填写到PKC助手-对应的加密key和iv框即可：

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/KaiQiJiaMi.png" alt="image-20230525225045195" style="zoom: 25%;" />

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/setKey.png" alt="image-20230525225553290" style="zoom: 25%;" />

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/setIv.png" alt="image-20230525225620287" style="zoom: 25%;" />

d. 最后点击推送测试看看，收到这个提示说明已经成功进行加密消息推送

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/testJiaMi.png" alt="image-20230525225710530" style="zoom: 25%;" />



# ③配置跳转URL “点击通知跳转指定URL”



**配置好的话，这样能够实现收到通知后，点击通知会自动跳转对应多开app，非常方便**

配置方法分两种，越狱和非越狱设备，越狱的非常简单，下面说非越狱的通过签名软件指定URL方法：

a. 以轻松签为例，打开应用-点击需要“多开的app”-查看文件位置

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/easySign_1.png" alt="image-20230525230456910" style="zoom:33%;" />

b. 点击WeChat - 查看文件

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/easySign_2.png" alt="image-20230525230329378" style="zoom: 25%;" />

c. 找到 Info.plist 文件，点击 属性编辑器

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/easySign_3.png" alt="image-20230525231107982" style="zoom:33%;" />

d. 重点 找到 `CFBundleURLTypes` 点击，再点击 `CFBundleURLSchemes`  再点击 `weixin` 

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/easySign_4.png" alt="image-20230525231317330" style="zoom:50%;" />

e. 弹窗修改Ta的值，可自己定义，这个就是作为URL跳转的链接，如改: pkc 跳转的链接就是 `pkc://`

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/easySign_5.png" alt="image-20230525231553834" style="zoom:50%;" />

f. 修改好后，返回签名安装即可。

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/easySign_6.png" alt="image-20230525231754908" style="zoom:33%;" />

g. 最后测试，可以直接打开浏览器输入pkc://访问，首次会提示一次“是否打开”，确认后，后面就不再提示了，直接打开。

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/easySign_7.png" alt="image-20230525232012238" style="zoom:50%;" />

h. 将pkc:// 填写到PKC助手-Bark推送-点击通知跳转指定URL

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/easySign_8.png" alt="image-20230525232233258" style="zoom:50%;" />

i.  Bark收到的通知下面会带有url，就是刚刚填写的pkc:// ，点击通知就会自动跳转多开的app（首次会提示，后面就直接跳转）

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/easySign_9.png" alt="image-20230525232330930" style="zoom:50%;" />

<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/easySign_10.png" alt="image-20230525232500748" style="zoom: 25%;" />



完成配置。



- 如果在info.plist用属性方式打开，找不到`CFBundleURLTypes`，那就自己通过“文本编辑器”打开拉到最后倒数第二行上面插入，添加以下代码，如图：

```
<key>CFBundleURLTypes</key>
<array>
  <dict>
    <key>CFBundleURLSchemes</key>
    <array>
      <string>pkc</string>
    </array>
  </dict>
</array>
```



<img src="https://raw.githubusercontent.com/curtinlv/PKCUpdateLog/main/img/easySign_11.png" alt="image-20230525232845427" style="zoom:33%;" />



end. 
