# intel nuc m15 笔记本
相关驱动：

<https://www.intel.com/content/www/us/en/products/sku/132221/intel-core-i51240p-processor-12m-cache-up-to-4-40-ghz/downloads.html>
# clash 的使用
### clash 项目地址
 <https://github.com/Dreamacro/clash>

linux 下查看cpu，并根据cpu的架构 Architecture 下载 对应的clash版本

    list cpu

## Windows下的准备操作

创建一个文件夹 `clash` ，把下载好的clash的gz包放进去

再放进去 个人的clash配置文件 `.yml` 和 `Country.mmdb`

现在`clash` 文件夹：
- `clash-linux-... .gz`
- `config.yml`
- `Country.mmdb`

## Ubuntu 下的操作
clash 文件夹通过u盘拷贝到 Ubuntu的 `Desktop` 下

将文件夹移动到 opt 下
```
    cd /opt 
    sudo mkdir clash

    sudo mv ~/Desktop/clash /opt

    cd /opt/clash
    gunzip clash-linux-... .gz
    mv clash-linux-... clash
```

测试

    ./clash --help


将clash设为守护进程
> 键入`cd /etc/systemd/system`
> 然后`sudo vim clash.service`
> 文件内容如下，直接复制粘贴即可(按i进入插入模式，然后shift+Insert粘贴)，然后退出保存(ESC + ZZ)
```shell
[Unit]
Description=clash-core
[Service]
Type=simple
ExecStart=/opt/clash/clash -f /opt/clash/config.yml -d /opt/clash/
[Install]
WantedBy=multi-user.target
```

 在终端中启用clash
```shell
#可将下面两行放入~/.bashrc中，否则仅对当次终端有效。
export http_proxy="http://127.0.0.1:7890"
export https_proxy="http://127.0.0.1:7890"

#查看环境变量
export

#启动clash
systemctl daemon-reload
systemctl start clash

#把clash设为开机自启
systemctl enable clash.service
#检查是否开机自启
systemctl is-enabled clash.service
```


 测试
```shell
curl -i google.com
```

 关闭clash
```shell
#终止clash服务
systemctl stop clash

#关闭开机自启
systemctl disable clash

#删除设置的环境变量
unset http_proxy
unset https_proxy
```

can kaoshipin

<https://www.bilibili.com/video/BV16z4y1n79T/?spm_id_from=333.1007.top_right_bar_window_history.content.click&vd_source=85c2f878f8175b8c035e77a07396553a>


# 中文输入法
## Fictx 5

- 参考博客：<https://fcitx-im.org/wiki/Fcitx_5/zh-cn>

- 对应视频：<https://muzing.top/posts/3fc249cf/>
  
经验：配置完，重启电脑后可以切换输入法

# LaTeX

## TeXlive
```
sudo apt-get install texlive-full
```
## 编辑器

### texstudio
```
sudo apt install texstudio
```

# 百度网盘
<https://pan.baidu.com/download#linux>

# 北太天元

官网地址 ：<https://www.baltamatica.com/download.html>


各种版本：<https://disk.pku.edu.cn/#/link/0EE816030B2E1A296FB029890388CD02?gns=41CD4566C310478980471F9C52E8C51B%2F5B93BC04B04148DAA3CA90083970528B>


# obs-studio

```
sudo add-apt-repository ppa:obsproject/obs-studio
sudo apt update
sudo apt install obs-studio
```

# VLC media player
```
sudo apt-get  install  vlc
```