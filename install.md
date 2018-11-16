
```bash
python --version # 版本
```

# 包管理器

```bash
sudo apt install python-pip
pip --version
```

升级后出现 “ImportError: cannot import name main” 错误时修复：

```py
# sudo vi /usr/bin/pip 
from pip import __main__
if __name__ == '__main__':
    sys.exit(__main__._main())
# 保存后关闭重开终端
```

# 虚拟环境

```bash
pip install virtualenv # 系统上网没有全局代理可能无法安装
# 测试过程发现还需要：
sudo apt install virtualenv
```

```bash
cd workspace
virtualenv --no-site-packages venv # 参数意味不从全局库中携带任何包
source venv/bin/activate # 激活虚拟环境
code . # 虚拟环境激活下启动 VSCODE， VSCODE 编译器环境即为当前虚拟环境
deactivate # 关闭虚拟环境
```

```bash
# 在虚拟环境激活情况下。
pip freeze > requirements.txt # 导出依赖库
pip install -r requirements.txt # 按照依赖库清单安装
```

# VSCODE 编辑器

__下载 .deb 文件安装：__

```bash
sudo dpkg -i vscode.deb
sudo apt-get install -f # 安装失败后执行，再次安装即可成功
code
```

__设置 VSCODE 为 中文：__

1. 搜索安装简体中文包插件： “zh-cn”
2. Ctrl + Shift + P > configure language
3. 修改 "locale":"zh-cn"
4. 保存并重启 code

__“ext install python” 安装官方的 python 插件：__

__在 VSCODE 中设置默认当前 python 编译器：__
"settings.json"设置： "python.formatting.provider": "yapf"


__在 VSCODE 中安装使用默认的 pylint：__

__使用 yapf 格式化代码：__

1. pip install yapf
2. "settings.json"设置： "python.formatting.provider": "yapf"
3. 右键-> "代码格式化（Ctrl + Shift + I）" 
