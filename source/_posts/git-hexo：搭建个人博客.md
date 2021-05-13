---
title: git-hexo：搭建个人博客
date: 2021-05-13 01:26:34
tags:web

---

# 搭建个人网站--git+hexo部署

#####   *计网老师布置了一个附加作业让我们搭建一个个人网站*，*所以就花了两个晚上搭建了一个很简单的*，*没有用到什么编程的个人博客网站*，借此博客记录一下。

## 一、学习链接

##### 1、我是跟着b站的一个视频部署的，那个up主讲得很详细了的，各种安装路径，注意事项都讲了很多的，大体安装过程都在那个视频里，链接如下：  

[超简单效果超好的个人网站博客搭建（对小白很友好）_哔哩哔哩 (゜-゜)つロ 干杯~-bilibili](https://www.bilibili.com/video/BV1je41147Ma?p=8&t=220)

#####  2、上面的视频虽然在本地可以直接运行了，但是不可以直接利用git部署，所以需要利用hexo的官方文档进行部署，链接如下：

[将 Hexo 部署到 GitHub Pages | Hexo](https://hexo.io/zh-cn/docs/github-pages)

##  二、注意事项以及我遇到的问题&解决方案

##### 1、b站那个视频是有对应文档的，up主放在评论区，可以自行下载。

##### 2、看b站那个视频时，注意！！！它的视频顺序有点乱，一定要先看p4再看p3，因为p4才跟p2接得上，且要先更改npm的镜像源，再进行下一步，小白一步错容易步步错，所以还是步步紧跟比较好。

##### 3、安装node.js时，配置环境变量一定要配对，他视频里有一篇博文的链接，那个很清楚，跟着博文一步一步做，最后一定要点确定！！！我就是增加了环境变量之后，但是没有按确定，后面因为环境变量出错就很烦，一定要配对.

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513015519995.png" alt="image-20210513015519995" style="zoom:50%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513015550349.png" alt="image-20210513015550349" style="zoom:50%;" />



就是最下面这个，你把前面的搞好了，这个一定要按确定，不能直接x掉。

##### 4、按照b站的视频一步步做完之后，就要利用git部署，不然只能是你自己用local4000访问，别人是访问不了的，单纯按照b站那个视频改一下url也是不行的，url要改，但是不仅仅要改（ ​手动​狗头:dog:），所以就要根据官方的那份文档进行部署。

+ 新建一个 repository。如果你希望你的站点能通过 `<你的 GitHub 用户名>.github.io` 域名访问，你的 repository 应该直接命名为 `<你的 GitHub 用户名>.github.io`。   

  --这个就是先新建一个仓库，最好是空的吧，就是连readme都没有那种。

  <img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513020526245.png" alt="image-20210513020526245" style="zoom:33%;" />

那个绿色的“New”看见了吗？点那个就可以先建一个仓库了。

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513020849685.png" alt="image-20210513020849685" style="zoom:50%;" />

然后填写一个仓库名（如：xx.github.io，xx你可以随便改，但是.github.io一定要有），然后什么都不勾选，直接点下面那个绿色的"Create repository"。

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513021047697.png" alt="image-20210513021047697" style="zoom:50%;" />

因为我们什么都没有选，所以这个仓库是全空的，全空的最好了，因为我们是有本地文件要上传的，所以选择上面那张图的第二段代码在git bash上运行就是了，然后部署的具体操作看这里吧，在git上执行这些命令，就是把你本地的文件上传到仓库里了，如果出错，看下面的链接：（反正我只出现了第一第二种错：  

[如何解决git上传文件出错[rejected\] master -> master (fetch first) error: failed to push some refs to '_way-up的博客-CSDN博客](https://blog.csdn.net/weixin_43264399/article/details/87350219)）

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513021428491.png" alt="image-20210513021428491" style="zoom:50%;" />



哦，还有这个，先改好再传，你要是先传了才看到这句，那就再传一遍呗：

​      将你的 Hexo 站点文件夹推送到 repository 中。默认情况下不应该 `public` 目录将不会被推送到 repository 中，你应该检查 `.gitignore` 文件中是否包含 `public` 一行，如果没有请加上。

+ 这段都是利用travis cli 进行自动部署的内容：（有一说一，官方文档写得实在不清楚）
  1. 将 [Travis CI](https://github.com/marketplace/travis-ci) 添加到你的 GitHub 账户中。
  2. 前往 GitHub 的 [Applications settings](https://github.com/settings/installations)，配置 Travis CI 权限，使其能够访问你的 repository。
  3. 你应该会被重定向到 Travis CI 的页面。如果没有，请 [手动前往](https://travis-ci.com/)。
  4. 在浏览器新建一个标签页，前往 GitHub [新建 Personal Access Token](https://github.com/settings/tokens)，只勾选 `repo` 的权限并生成一个新的 Token。Token 生成后请复制并保存好。
  5. 回到 Travis CI，前往你的 repository 的设置页面，在 **Environment Variables** 下新建一个环境变量，**Name** 为 `GH_TOKEN`，**Value** 为刚才你在 GitHub 生成的 Token。确保 **DISPLAY VALUE IN BUILD LOG** 保持 **不被勾选** 避免你的 Token 泄漏。点击 **Add** 保存。
  6. 在你的 Hexo 站点文件夹中新建一个 `.travis.yml` 文件：
  7. 将 `.travis.yml` 推送到 repository 中。Travis CI 应该会自动开始运行，并将生成的文件推送到同一 repository 下的 `gh-pages` 分支下
  8. 在 GitHub 中前往你的 repository 的设置页面，修改 `GitHub Pages` 的部署分支为 `gh-pages`。
  9. 前往 `https://<你的 GitHub 用户名>.github.io` 查看你的站点是否可以访问。这可能需要一些时间



###### 存在问题

+ 怎么添加到github账户：

  点上面那个链接，进去，然后选择免费的：就下面那张图蓝色那个。

  <img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513022250338.png" alt="image-20210513022250338" style="zoom:33%;" />



然后点完之后，应该就是添加了吧，具体的页面我截不了，因为我已经添加完了，反正最后能出现这个就行

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513022547965.png" alt="image-20210513022547965" style="zoom:50%;" />

+ 进入cli 的页面，配置好token（就按官网的步骤就行，很简单的），然后修改环境变量，在这：

  <img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513022816456.png" alt="image-20210513022816456" style="zoom: 50%;" />

<img src="C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513022848195.png" alt="image-20210513022848195" style="zoom: 50%;" />

+ 配置好token 之后，就到最后那个.travis.yml文件，复制官网的那一段代码之后，记得把node.js的版本改成你的版本，就下面那个：

  ![image-20210513023036602](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513023036602.png)

哦，还有一个：这个要改成你上传的那个文件夹，这个分支一般叫main ，就上面你新建仓库的时候，那个git branch M main，上面写了啥，这里就写啥。

![image-20210513023343442](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513023343442.png)

至于输出的文件分支，就改成官网那个gh-pages分支就行。

![image-20210513023553643](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513023553643.png)



但是前面的步骤是没有新建分支gh-pages的，所以你要先建一个，如下图，从master创建一个分支

![image-20210513105331442](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513105331442.png)

+ 按照这个配完，应该是可以的，如果你的文件上传了√，就看你生成的那个branch是不是public的文件夹的内容，public文件夹的目录也在下面了（这个public其实就是之前在.gitignore那里注释掉的文件夹，因为你上传到git之后，它会给你生成，所以我们就不上传），如果这个也对的话，那就完成了，直接去看http://XX.github.io就好了，应该就显示得跟你本地运行一样的页面了。

  ![image-20210513025000246](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20210513025000246.png)

  如果不行哈哈哈，恭喜你，你跟我一样，出现未知故障。。。就要放弃cli部署了

  ##### 没办法，我舍友一会就搞完了，而我总是出现奇奇怪怪的错误，摊手，运气太好了

  方法：就是你再新建一个仓库，然后直接把你之前没上传的那个public文件传上去（这里也给它创建一个分支叫source就好了，跟gh-pages一个道理），新建仓库的过程跟上面一样，上传的过程也跟上面一样，链接分支的过程都一样，无非就是再搞一次。。。然后执行git push -u origin master/xx/main 那个命令（master/xx/main这个是你起的仓库分支名）

这样就可以了，反正我可以了，如果你们出错，那就只能多百度了，遇事不决找度娘，祝你好运。