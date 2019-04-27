# Dell vostro 3667 黑苹果安装日记
黑苹果的安装，对于我等小白来说，版本的选择很重要，其实黑苹果的系统和白苹果是一样的，所谓的版本，是指的用于引导系统启动的Clover配置文件。对于我的Dell  vostro 3667的硬件配置来说，有些网上的黑苹果版本，压根一次都无法启动，我比较幸运，第一次就下对了版本。正常装上后会发现没有显卡，在配置显卡的过程中由于过于自信，没有严格按照网上的教程去弄，走了一些弯路。

## Dell vostro 3667 系统硬件

CPU | Intel i3 6100
----|---------------
GPU | intel hd 530
memory | 8G


## 系统选择
所采用的黑苹果镜像来自高校内的PT网站：https://npupt.com/details.php?id=144333&hit=1 不方便下载的可以联系我，我传到百度盘。
![黑苹果镜像](/pic1.png)


## 系统安装
### 安装前检查
1:黑苹果加载显卡后只支持hdmi接口输出。2:请确定当前的磁盘分区表格式为EFI以及当前操作系统的引导方式为EFI，因为苹果系统只支持EFI引导

### 安装U盘制作
windows上 | 使用TransMac Ultraiso 等软件将苹果的dmg镜像写入到U盘，注意U盘中的所有数据都会被丢失
-----------------------|-----------------------------------------------------------------------------
Linux上（以Ubuntu为例）| sudo apt install dmg2img。 使用dmg2img命令将dmg镜像转成img格式后使用dd命令或者直接双击img文件写入U盘

### 安装镜像bug修正
该安装包中默认clover启动时间为0，会造成很多问题。 在windows上通过diskgennius工具将U盘EFI\CLover\config.plist文件中boot项目中的启动等待时间设置为0.  Linux上可以挂在U盘的EFI分区按照相同方法设置。

### 安装过程
重启按F12。选择EFI模式的U盘引导启动。进入变色龙选择画面后，按o键，选Config中的HD530的那个Config启动，正常格式化一个分区为苹果格式，正常安装，重启后继续F12进U盘，Config依旧HD530，选安装到的那个分区启动，继续完成安装，第二次启动后可能装了几秒就自动重新启动，不要慌，再来一次即可安装完成。

### 显卡驱动
装好后会发现有线网卡正常驱动，声卡正常驱动，显卡没驱动，蓝牙没驱动，wifi没驱动。
显卡驱动请严格按照https://blog.daliansky.net/Intel-FB-Patcher-tutorial-and-insertion-pose.html 给缓冲帧打补丁的部分操作，不要进行任何自作聪明的操作，即可驱动显卡，需要的CloverConfigurator，Hackintool工具可以在本github项目中下载，也可以在那个网页作者的博客中找找。

### NTFS磁盘读写
即使是白苹果，一样无法写NTFS，需要个免费的小软件解决：https://mounty.app




### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/leixd1994/leixd1994.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
