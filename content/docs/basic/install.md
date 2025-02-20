+++
title = "安装"
date = 2025-02-17T11:55:36+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

# Go

以下是针对多种操作系统安装最新版Go、配置环境变量及管理多版本的详细指南：

---

### **一、通用步骤：安装最新版Go**
#### **1. 下载并安装Go**
访问 [Go官方下载页面](https://go.dev/dl/)，根据系统选择对应的二进制包（如 `goX.XX.X.linux-amd64.tar.gz`）。

#### **2. 解压并设置路径**
```bash
# 以 Linux/macOS 为例（版本号替换为实际值）
sudo rm -rf /usr/local/go # 若旧版本存在
sudo tar -C /usr/local -xzf goX.XX.X.linux-amd64.tar.gz
```

#### **3. 配置环境变量**
编辑用户配置文件（如 `~/.bashrc`, `~/.zshrc`, 或 `~/.profile`）：
```bash
export PATH=$PATH:/usr/local/go/bin
export GOPATH=$HOME/go
export GOPROXY=https://goproxy.cn,direct # 国内镜像加速
export GO111MODULE=on
```
运行 `source ~/.bashrc` 生效。

#### **4. 验证安装**
```bash
go version
# 输出类似：go version go1.21.0 linux/amd64
```

---

### **二、各系统具体安装方法**
#### **1. Windows 11**
- **方法1（推荐）**：  
  1. 下载 `.msi` 安装程序，双击安装（默认路径 `C:\Go`）。  
  2. 系统自动添加 `C:\Go\bin` 到 `PATH`。  
  3. 配置环境变量：  
     - 右键“此电脑” → 属性 → 高级系统设置 → 环境变量 → 新建用户变量：  
       - `GOPATH`: `%USERPROFILE%\go`  
       - `GOPROXY`: `https://goproxy.cn,direct`

- **方法2（手动安装）**：  
  1. 下载 `.zip` 包，解压到 `C:\Go`。  
  2. 手动添加 `C:\Go\bin` 到 `PATH`。

#### **2. macOS**
- **方法1（推荐）**：使用 Homebrew：
  ```bash
  brew update
  brew install go
  ```
- **方法2（手动安装）**：同通用步骤。

#### **3. RHEL/AlmaLinux/Rocky Linux**
```bash
# 安装依赖
sudo dnf install -y tar gzip
# 下载并解压（以 amd64 架构为例）
wget https://go.dev/dl/goX.XX.X.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf goX.XX.X.linux-amd64.tar.gz
# 配置环境变量（见通用步骤）
```

#### **4. Ubuntu 24.04/Ubuntu Server**
```bash
# 安装依赖
sudo apt update && sudo apt install -y wget tar
# 下载并解压
wget https://go.dev/dl/goX.XX.X.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf goX.XX.X.linux-amd64.tar.gz
# 配置环境变量（见通用步骤）
```

#### **5. Alpine Linux**
```bash
# 安装依赖
apk add --no-cache wget tar
# 下载并解压（注意 Alpine 通常使用 amd64 或 arm64）
wget https://go.dev/dl/goX.XX.X.linux-amd64.tar.gz
tar -C /usr/local -xzf goX.XX.X.linux-amd64.tar.gz
# 配置环境变量（见通用步骤）
```

---

### **三、多版本管理**
#### **1. 使用 `go install` 安装其他版本**
```bash
# 安装指定版本（如 1.20.7）
go install golang.org/dl/go1.20.7@latest
go1.20.7 download
# 使用指定版本
go1.20.7 version
```

#### **2. 使用版本管理工具（如 `gvm`）**
```bash
# 安装 gvm
bash < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer)
# 安装多个版本
gvm install go1.21.0
gvm install go1.20.7
# 切换版本
gvm use go1.21.0
```

#### **3. 手动切换（推荐）**
- 将不同版本解压到不同目录（如 `/usr/local/go1.21.0` 和 `/usr/local/go1.20.7`）。  
- 通过修改 `PATH` 切换版本：
  ```bash
  # 临时切换
  export PATH=/usr/local/go1.21.0/bin:$PATH
  # 永久切换（编辑 ~/.bashrc）
  echo 'export PATH=/usr/local/go1.21.0/bin:$PATH' >> ~/.bashrc
  ```

---

### **四、高级配置**
#### **1. 私有仓库配置**
```bash
export GOPRIVATE=git.mycompany.com,github.com/myorg
```

#### **2. 禁用模块缓存（开发调试）**
```bash
export GOMODCACHE=$HOME/go/mod
```

#### **3. 交叉编译配置**
```bash
# 编译 Windows 64 位程序
GOOS=windows GOARCH=amd64 go build -o app.exe
```

---

### **五、验证与测试**
```bash
# 创建测试项目
mkdir -p $GOPATH/src/hello && cd $GOPATH/src/hello
echo 'package main\nimport "fmt"\nfunc main() { fmt.Println("Hello, Go!") }' > main.go
# 构建并运行
go run main.go
```

---

### **总结**
- **统一环境变量**：确保 `GOPATH` 和 `GOPROXY` 在所有系统中配置一致。  
- **多版本管理**：推荐使用 `gvm` 或手动切换目录，避免路径冲突。  
- **国内用户**：务必设置 `GOPROXY=https://goproxy.cn` 加速依赖下载。



## Python

以下是针对多操作系统安装最新版 Python、配置国内镜像及管理多版本的详细指南：

---

### **一、通用步骤：安装最新版 Python**
#### **1. 下载并安装 Python**
访问 [Python 官方下载页面](https://www.python.org/downloads/)，选择对应系统的安装包（或使用包管理工具）。

#### **2. 验证安装**
```bash
python3 --version  # 或 python --version（Windows）
pip3 --version     # 或 pip --version
```

---

### **二、各系统具体安装方法**
#### **1. Windows 11**
- **方法 1（推荐）**：  
  1. 下载 `.exe` 安装程序，勾选 **Add Python to PATH**。  
  2. 安装完成后，验证环境变量是否生效。

- **方法 2（手动安装）**：  
  1. 解压安装包到 `C:\PythonXX`（如 `C:\Python311`）。  
  2. 手动添加路径 `C:\PythonXX` 和 `C:\PythonXX\Scripts` 到系统 `PATH`。

#### **2. macOS**
- **方法 1（推荐）**：使用 Homebrew：
  ```bash
  brew update
  brew install python@3.11  # 指定版本
  ```
- **方法 2（官方安装包）**：  
  下载 `.pkg` 文件安装，自动配置环境变量。

#### **3. RHEL/AlmaLinux/Rocky Linux**
```bash
# 启用 EPEL 仓库
sudo dnf install epel-release
# 安装 Python 3.11
sudo dnf install python3.11
# 验证
python3.11 --version
```

#### **4. Ubuntu 24.04/Ubuntu Server**
```bash
# 默认仓库可能包含较新版本，若需最新版：
sudo add-apt-repository ppa:deadsnakes/ppa  # 添加第三方仓库
sudo apt update
sudo apt install python3.11
```

#### **5. Alpine Linux**
```bash
# Alpine 默认使用 musl 库，需从源码编译
apk add --no-cache build-base zlib-dev libffi-dev openssl-dev
wget https://www.python.org/ftp/python/3.11.4/Python-3.11.4.tgz
tar xzf Python-3.11.4.tgz
cd Python-3.11.4
./configure --enable-optimizations
make -j$(nproc)
sudo make install
```

---

### **三、配置国内镜像加速**
#### **1. 临时使用镜像**
```bash
pip install numpy -i https://pypi.tuna.tsinghua.edu.cn/simple
```

#### **2. 永久配置镜像**
- **Linux/macOS**：  
  创建或修改 `~/.config/pip/pip.conf`（新版本 pip 默认遵循 XDG 规范，优先使用此路径。旧路径 `~/.pip/pip.conf` 仍兼容，但已不推荐。）：
  
  ```ini
  [global]
  index-url = https://pypi.tuna.tsinghua.edu.cn/simple
  trusted-host = pypi.tuna.tsinghua.edu.cn
  ```
  
- **Windows**：  
  在 `%APPDATA%\pip\pip.ini`（即 `C:\Users\<用户名>\AppData\Roaming\pip\pip.ini`）（`%APPDATA%`表示环境变量：`$env:APPDATA`，其值为：`C:\Users\用户名\AppData\Roaming`） 中添加同上内容。
  
  > 需显示隐藏文件夹才能看到 `AppData` 目录。

#### **3. 虚拟环境镜像配置**
在创建虚拟环境时指定镜像：
```bash
python -m venv myenv --system-site-packages --pip https://pypi.tuna.tsinghua.edu.cn/simple
```

---

### **四、多版本 Python 管理**
#### **1. 使用 `pyenv`（跨平台推荐）**
```bash
# 安装 pyenv（Linux/macOS）
curl https://pyenv.run | bash
# 添加到 Shell 配置文件（如 ~/.bashrc）
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
source ~/.bashrc

# 安装多版本
pyenv install 3.11.4
pyenv install 3.8.16

# 切换全局版本
pyenv global 3.11.4

# 切换项目局部版本
cd myproject
pyenv local 3.8.16
```

#### **2. Windows 多版本管理**
- **Python Launcher**：  
  Windows 默认安装的 `py` 命令可管理多版本：
  ```powershell
  py -3.11 -m pip install numpy  # 使用 Python 3.11
  py -3.8 script.py             # 使用 Python 3.8
  ```

#### **3. Linux 手动管理**
```bash
# 安装不同版本到不同路径
sudo apt install python3.9 python3.10
# 使用 update-alternatives 切换默认版本
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.11 1
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.9 2
sudo update-alternatives --config python3  # 交互式选择版本
```

---

### **五、其他关键配置**
#### **1. 虚拟环境工具**
```bash
# 使用 venv（Python 3.3+ 内置）
python -m venv myenv
source myenv/bin/activate  # Linux/macOS
myenv\Scripts\activate     # Windows

# 使用 virtualenv（更灵活）
pip install virtualenv
virtualenv myenv
```

#### **2. 依赖管理**
```bash
# 生成 requirements.txt
pip freeze > requirements.txt
# 安装依赖
pip install -r requirements.txt -i https://mirrors.aliyun.com/pypi/simple/
```

#### **3. 开发工具链**
```bash
# 安装常用开发库
pip install numpy pandas matplotlib jupyterlab -i https://pypi.tuna.tsinghua.edu.cn/simple
```

---

### **六、验证与调试**
```bash
# 检查 Python 版本
python --version

# 检查 pip 镜像是否生效
pip config get global.index-url

# 测试依赖安装
pip install requests
python -c "import requests; print(requests.__version__)"
```

---

### **七、总结**
- **镜像加速**：优先使用清华、阿里云或中科大镜像提升下载速度。  
- **多版本管理**：  
  - **Linux/macOS**：推荐 `pyenv`，支持动态切换版本。  
  - **Windows**：使用 `py` 命令或手动调整环境变量。  
- **虚拟环境**：始终为项目创建独立环境，避免依赖冲突。  
- **企业级系统（RHEL/AlmaLinux）**：优先通过 EPEL 或 SCL 安装，确保系统稳定性。

## Java

以下是针对多种操作系统安装最新版 Java 和 Java 8、配置国内镜像及管理多版本的详细指南：

---

### **一、通用步骤：安装最新版 Java**
#### **1. 下载并安装 Java**
- **Oracle JDK**：需从 [Oracle官网](https://www.oracle.com/java/technologies/downloads/) 下载（需登录）。
- **OpenJDK**：推荐使用社区维护的发行版（如 Adoptium、Azul Zulu、Amazon Corretto）。

#### **2. 配置环境变量**
```bash
# 设置 JAVA_HOME 和 PATH（示例路径：/usr/lib/jvm/jdk-21）
export JAVA_HOME=/path/to/jdk
export PATH=$JAVA_HOME/bin:$PATH
```

---

### **二、各系统具体安装方法**
#### **1. Windows 11**
- **方法 1（手动安装）**：  
  
  1. 访问国内镜像下载JDK：
     - [清华镜像站](https://mirrors.tuna.tsinghua.edu.cn/Adoptium/)
     - 下载`jdk-21_windows-x64_bin.zip`和`jdk-8u401-windows-x64.exe`
  2. 解压/安装到不同目录（如`C:\Java\jdk-21`和`C:\Java\jdk1.8.0_401`）
  3. 配置环境变量：  
     - 新建系统变量 `JAVA_HOME`，值为 JDK 安装路径。  
     - 将 `%JAVA_HOME%\bin` 添加到 `PATH` 中。  
  
- **方法 2（包管理器）**：  
  使用 [Scoop](https://scoop.sh/)：  
  
  ```powershell
  scoop bucket add java
  scoop install temurin-lts-jdk  # 安装 OpenJDK LTS 版本（如 JDK 21）
  ```
- **方法 3 使用Chocolatey（包管理器）**

```powershell
# 安装Chocolatey
Set-ExecutionPolicy Bypass -Scope Process -Force
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

# 安装多版本JDK
choco install temurin21jdk --version=21.0.2
choco install temurin8jdk --version=8.0.401
```

> 
>

#### **2. macOS**
- **方法 1（Homebrew）**：  
  ```bash
  brew tap homebrew/cask-versions
  brew install --cask temurin  # 最新版 OpenJDK
  brew install --cask temurin8 # Java 8
  ```
- **方法 2（手动安装）**：  
  下载 `.dmg` 文件安装，路径通常为 `/Library/Java/JavaVirtualMachines/jdk-21.jdk`。

#### **3. RHEL/AlmaLinux/Rocky Linux**
```bash
# 安装 OpenJDK（最新版）
sudo dnf install java-21-openjdk-devel

# 安装 Java 8
sudo dnf install java-1.8.0-openjdk-devel

# 验证版本
java -version
```

#### **4. Ubuntu 24.04/Ubuntu Server**
```bash
# 添加 OpenJDK 官方仓库
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt update

# 安装最新版 OpenJDK
sudo apt install openjdk-21-jdk

# 安装 Java 8
sudo apt install openjdk-8-jdk
```

#### **5. Alpine Linux**
```bash
# 安装 OpenJDK 21
apk add openjdk21

# 安装 Java 8（需启用社区仓库）
echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories
apk update
apk add openjdk8
```

---

### **三、配置国内镜像（Maven/Gradle）**
#### **1. Maven 镜像配置**
编辑 `~/.m2/settings.xml`：
```xml
<mirrors>
  <mirror>
    <id>aliyun</id>
    <name>Aliyun Maven Mirror</name>
    <url>https://maven.aliyun.com/repository/public</url>
    <mirrorOf>central</mirrorOf>
  </mirror>
</mirrors>
```

#### **2. Gradle 镜像配置**
修改 `~/.gradle/init.gradle`：
```groovy
allprojects {
    repositories {
        maven { url 'https://maven.aliyun.com/repository/public' }
        mavenCentral()
    }
}
```

---

### **四、多版本 Java 管理**
#### **1. Linux/macOS：使用 `update-alternatives`**
```bash
# 注册 Java 版本
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-21/bin/java 100
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk1.8.0_381/bin/java 50

# 交互式切换版本
sudo update-alternatives --config java
```

#### **2. 使用 SDKMAN!（跨平台推荐）**
```bash
# 安装 SDKMAN!
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"

# 安装多版本 JDK
sdk install java 21.0.1-tem
sdk install java 8.0.382-tem

# 切换版本
sdk use java 21.0.1-tem
```

#### **3. Windows：手动切换**
- 修改环境变量 `JAVA_HOME` 指向不同 JDK 路径（如 `C:\Program Files\Java\jdk1.8.0_381`）。  
- 使用批处理脚本动态切换：
  ```bat
  @echo off
  set JAVA_HOME=C:\Program Files\Java\jdk-21
  set PATH=%JAVA_HOME%\bin;%PATH%
  ```

---

### **五、其他关键配置**
#### **1. 环境变量优先级**
- 确保 `JAVA_HOME` 指向当前使用的 JDK 路径。  
- 验证命令：  
  ```bash
  echo $JAVA_HOME   # Linux/macOS
  echo %JAVA_HOME%  # Windows
  ```

#### **2. 检查默认版本**
```bash
java -version
javac -version
```

#### **3. 企业级系统（RHEL/AlmaLinux）**
- 使用 `alternatives` 命令管理多版本，确保与系统服务兼容。

---

### **六、总结**
- **镜像加速**：优先使用阿里云或华为云镜像提升依赖下载速度。  
- **多版本管理**：  
  - **Linux/macOS**：推荐 `update-alternatives` 或 `SDKMAN!`。  
  - **Windows**：手动修改环境变量或使用 SDKMAN!。  
- **企业环境**：建议使用 OpenJDK 长期支持版本（如 JDK 21 LTS）。  
- **Alpine Linux**：注意依赖 musl libc，选择兼容的 JDK 版本。



## Rust

以下是针对多种操作系统安装最新版 Rust、配置国内镜像及管理多版本的详细指南：

---

### **一、通用步骤：安装最新版 Rust**
#### **1. 使用 `rustup` 安装（推荐）**
```bash
# 所有系统通用命令（Windows 需使用 PowerShell 或 CMD）
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
- 安装过程中按提示选择默认选项（默认安装 `stable` 工具链）。
- 安装完成后运行：
  ```bash
  source $HOME/.cargo/env  # Linux/macOS
  refreshenv               # Windows（可能需要重启终端）
  ```

#### **2. 验证安装**
```bash
rustc --version  # 输出示例：rustc 1.77.0 (aed9d8b44 2024-03-27)
cargo --version
```

---

### **二、各系统具体安装方法**
#### **1. Windows 11**
- **依赖安装**：  安装 [Visual Studio Build Tools](https://visualstudio.microsoft.com/visual-cpp-build-tools/) 并勾选 **C++ 构建工具** 和 **Windows SDK**。
- **安装 Rust**：  运行 `rustup-init.exe`（从 [rustup.rs](https://rustup.rs/) 下载）并按提示操作。
- **配置环境变量**：  安装程序会自动添加 `%USERPROFILE%\.cargo\bin` 到 `PATH`。

#### **2. macOS**
- **依赖安装**：  安装 Xcode 命令行工具：
  
  ```bash
  xcode-select --install
  ```
- **安装 Rust**：  同通用步骤的 `rustup` 命令。

#### **3. RHEL/AlmaLinux/Rocky Linux**
```bash
# 安装依赖
sudo dnf install -y curl gcc make openssl-devel

# 安装 Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

#### **4. Ubuntu 24.04/Ubuntu Server**
```bash
# 安装依赖
sudo apt update && sudo apt install -y curl build-essential

# 安装 Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

#### **5. Alpine Linux**
```bash
# 安装依赖
apk add --no-cache curl gcc musl-dev

# 安装 Rust（指定目标为 musl）
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
rustup target add x86_64-unknown-linux-musl  # 支持静态编译
```

---

### **三、配置国内镜像加速**
#### **1. 配置 Cargo 镜像**
创建或修改 `~/.cargo/config` 文件：
```toml
[source.crates-io]
replace-with = 'ustc'  # 或 tuna、rsproxy

# 中科大镜像
[source.ustc]
registry = "sparse+https://mirrors.ustc.edu.cn/crates.io-index/"

# 清华大学镜像
[source.tuna]
registry = "sparse+https://mirrors.tuna.tsinghua.edu.cn/git/crates.io-index.git"

# Rust官方镜像（中国区 CDN）
[source.rsproxy]
registry = "sparse+https://rsproxy.cn/crates.io-index"
```

#### **2. 配置 Rustup 镜像（可选）**
```bash
# 设置环境变量（临时生效）
export RUSTUP_DIST_SERVER=https://mirrors.ustc.edu.cn/rust-static
export RUSTUP_UPDATE_ROOT=https://mirrors.ustc.edu.cn/rust-static/rustup

# 永久生效（写入 Shell 配置文件）
echo 'export RUSTUP_DIST_SERVER="https://mirrors.ustc.edu.cn/rust-static"' >> ~/.bashrc
echo 'export RUSTUP_UPDATE_ROOT="https://mirrors.ustc.edu.cn/rust-static/rustup"' >> ~/.bashrc
source ~/.bashrc
```

---

### **四、多版本 Rust 管理**
#### **1. 使用 `rustup` 管理工具链**
```bash
# 安装指定版本（如 1.76.0）
rustup install 1.76.0

# 安装其他工具链（nightly、beta）
rustup install nightly

# 列出已安装版本
rustup toolchain list

# 切换默认版本
rustup default 1.76.0

# 临时使用特定版本
cargo +nightly build
```

#### **2. 项目级版本控制**
在项目根目录创建 `rust-toolchain` 文件：
```toml
[toolchain]
channel = "1.76.0"  # 或 "nightly"
```

---

### **五、其他关键配置**
#### **1. 构建优化**
```bash
# 在 `~/.cargo/config` 中添加：
[build]
target-dir = "target"  # 统一构建目录
rustflags = ["-C", "target-cpu=native"]  # 启用本地 CPU 优化
```

#### **2. 安装常用工具**
```bash
# 代码格式化
rustup component add rustfmt

# 代码检查
rustup component add clippy

# 文档生成
cargo install cargo-doc
```

#### **3. 跨平台编译**
```bash
# 安装目标平台支持（如 Windows）
rustup target add x86_64-pc-windows-gnu

# 交叉编译示例
cargo build --target x86_64-pc-windows-gnu
```

---

### **六、验证与调试**
```bash
# 检查镜像是否生效
cargo search serde  # 观察下载速度

# 创建测试项目
cargo new hello_world
cd hello_world
cargo run

# 检查工具链版本
rustup show
```

---

### **七、总结**
- **安装统一性**：所有系统均可通过 `rustup` 一键安装，无需手动管理路径。  
- **镜像加速**：优先使用中科大或清华镜像提升依赖下载速度。  
- **多版本管理**：  
  - 使用 `rustup` 切换全局或项目级版本。  
  - 通过 `rust-toolchain` 文件固定项目版本。  
- **企业级系统（RHEL/AlmaLinux）**：注意安装开发依赖（如 `openssl-devel`）。  
- **Alpine Linux**：需额外安装 `musl-dev` 支持静态编译。



## C/C++

---

### **一、Windows 11**
#### **1. 安装最新工具链**
*方法1：MSVC（Visual Studio）*
1. 下载 [Visual Studio](https://visualstudio.microsoft.com/) 选择"C++桌面开发"
2. 勾选最新MSVC工具链（如MSVC v143）和Windows SDK

*方法2：MinGW-w64*
```powershell
# 使用Scoop包管理器（清华镜像）
irm get.scoop.sh | iex
scoop install mingw -a 64bit
scoop bucket add versions
scoop install gcc13
```

#### **2. 多版本管理**
```powershell
# 安装多个GCC版本
scoop install gcc12 gcc13

# 切换版本（通过环境变量）
$env:Path = "C:\Users\用户\scoop\apps\gcc13\current\bin;" + $env:Path
```

#### **3. 镜像配置**
```powershell
# 设置Scoop镜像
scoop config SCOOP_REPO 'https://mirror.nju.edu.cn/git/scoop-skygqi/'
scoop bucket add main https://mirror.nju.edu.cn/git/scoop-main/
```

---

### **二、macOS**
#### **1. 安装最新工具链**
```bash
# 使用Homebrew（中科大镜像）
echo 'export HOMEBREW_API_DOMAIN="https://mirrors.ustc.edu.cn/homebrew-bottles/api"' >> ~/.zshrc
echo 'export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.ustc.edu.cn/homebrew-bottles"' >> ~/.zshrc
source ~/.zshrc

brew install llvm
brew install gcc
```

#### **2. 多版本管理**
```bash
# 安装多版本GCC
brew install gcc@13 gcc@12

# 切换版本（以GCC13为例）
export PATH="/usr/local/opt/gcc@13/bin:$PATH"
export LDFLAGS="-L/usr/local/opt/gcc@13/lib"
export CPPFLAGS="-I/usr/local/opt/gcc@13/include"
```

---

### **三、RHEL 9/AlmaLinux/Rocky Linux**
#### **1. 安装最新工具链**
```bash
# 启用EPEL和SCL（清华大学镜像）
sudo sed -e 's|^mirrorlist=|#mirrorlist=|g' \
         -e 's|^#baseurl=http://mirror.centos.org|baseurl=https://mirrors.tuna.tsinghua.edu.cn/centos|g' \
         -i /etc/yum.repos.d/CentOS-*.repo

sudo dnf install epel-release
sudo dnf install centos-release-scl

# 安装开发工具集
sudo dnf groupinstall "Development Tools"
sudo dnf install gcc-toolset-13
```

#### **2. 多版本管理**
```bash
# 启用SCL环境
scl enable gcc-toolset-13 bash

# 查看可用版本
scl -l
```

---

### **四、Ubuntu 24.04/Ubuntu Server**
#### **1. 安装最新工具链**
```bash
# 配置清华源
sudo sed -i 's/archive.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list

sudo apt update
sudo apt install build-essential gcc-13 g++-13
```

#### **2. 多版本管理**
```bash
# 设置alternatives
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-13 100
sudo update-alternatives --install /usr/bin/gcc gcc /usr/bin/gcc-12 90

# 交互式切换
sudo update-alternatives --config gcc
```

---

### **五、Alpine Linux**
#### **1. 安装最新工具链**
```bash
# 配置阿里云镜像
echo "http://mirrors.aliyun.com/alpine/latest-stable/main" > /etc/apk/repositories
echo "http://mirrors.aliyun.com/alpine/latest-stable/community" >> /etc/apk/repositories

apk update
apk add build-base clang
```

#### **2. 多版本管理**
```bash
# 安装GCC12
apk add gcc12 g++12

# 创建符号链接
ln -sf /usr/bin/gcc-12 /usr/local/bin/gcc
```

---

### **六、通用配置**
#### **跨平台构建工具**
```bash
# CMake配置镜像（CPM.cmake）
set(CPM_USE_LOCAL_PACKAGES TRUE)
CPMAddPackage(
  NAME Catch2
  GIT_REPOSITORY https://hub.nuaa.cf/catchorg/Catch2.git
  GIT_TAG        v3.5.0
)
```

#### **编译环境验证**
```bash
# 验证GCC版本
gcc --version

# 简单测试程序
echo -e '#include <iostream>\nint main(){std::cout<<"Hello\\n";}' > test.cpp
g++ -o test test.cpp && ./test
```

---

### **七、高级工具链管理**
#### **Docker多版本环境**
```dockerfile
# 多阶段构建示例
FROM gcc:13-bookworm AS builder
COPY . .
RUN make

FROM gcc:12-bullseye AS runtime
COPY --from=builder /app .
CMD ["./app"]
```

#### **conda环境管理**
```bash
conda create -n cpp20 gcc=13
conda activate cpp20
```

---

### **八、注意事项**
1. **ABI兼容性**：
   - 混合使用不同版本的运行时库可能导致崩溃
   - 推荐使用 `-static-libstdc++` 静态链接标准库

2. **内核头文件兼容**：
   ```bash
   # Alpine需要单独安装
   apk add linux-headers
   ```

3. **Windows路径处理**：
   - 使用 `/I` 代替 `-I`（MSVC）
   - 路径分隔符使用反斜杠 `\`

通过以上步骤，可在各平台搭建灵活的多版本C/C++开发环境。生产环境建议使用Docker容器化方案保证一致性。



## JavaScript





## TypeScript



### **Windows 11**
#### **安装Node.js环境**
1. 使用nvm-windows管理Node版本：
   ```powershell
   curl -o nvm-setup.exe https://mirrors.tencent.com/nodejs-release/nvm/v1.1.12/nvm-setup.exe
   ./nvm-setup.exe
   nvm install 20 --arch=x64 --proxy=http://mirrors.tencent.com
   nvm use 20
   ```

#### **配置国内镜像**
```powershell
npm config set registry https://registry.npmmirror.com
npm config set disturl https://mirrors.tencent.com/nodejs-release/
```

#### **安装最新TypeScript**
```powershell
npm install -g typescript@latest
tsc --version
```

#### **多版本管理**
```powershell
npm install -g typescript@4.9.5
npx -p typescript@4.9.5 tsc --version
```

### **macOS**
#### **安装Node.js环境**
```bash
export NVM_NODEJS_ORG_MIRROR=https://mirrors.tuna.tsinghua.edu.cn/nodejs-release/
curl -o- https://mirrors.tuna.tsinghua.edu.cn/nvm/latest/install.sh | bash
nvm install --lts
```

#### **配置镜像与安装TS**
```bash
npm config set registry https://registry.npmmirror.com
npm install -g typescript@latest
```

#### **多版本管理**
```bash
mkdir project-ts5 && cd project-ts5
npm install typescript@5.0
npm link typescript@5.0
```

### **RHEL/AlmaLinux/Rocky Linux**
#### **安装Node.js**
```bash
curl -sL https://mirrors.tuna.tsinghua.edu.cn/nodesource/setup_20.x | sudo bash -
sudo dnf install -y nodejs
```

#### **配置与安装**
```bash
npm config set registry https://registry.npmmirror.com
sudo npm install -g typescript@latest
```

#### **多版本管理**
```bash
sudo alternatives --install /usr/bin/tsc tsc /usr/lib/node_modules/typescript/bin/tsc 100
sudo alternatives --config tsc
```

### **Ubuntu 24.04/Server**
#### **安装Node.js**
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs
```

#### **配置与安装**
```bash
npm config set registry https://registry.npmmirror.com
sudo npm install -g typescript@latest
```

#### **多版本共存**
```bash
sudo npm install -g typescript@5.0 --prefix /usr/local/ts5
export PATH="/usr/local/ts5/bin:$PATH"
```

### **Alpine Linux**
#### **安装Node.js**
```bash
echo "http://mirrors.aliyun.com/alpine/latest-stable/main" > /etc/apk/repositories
apk update
apk add nodejs npm
```

#### **配置与安装**
```bash
npm config set registry https://registry.npmmirror.com
npm install -g typescript@latest
```

#### **多版本管理**
```bash
mkdir ts4 && cd ts4
npm install typescript@4.9
alias ts4='$(npm bin)/tsc'
```

### **通用多版本方案**
#### **项目级版本控制**
```bash
npm init -y
npm install typescript@5.0
npx tsc --version
```

#### **版本切换工具**
```bash
npm install -g ts-node@10.9.1
ts-node -v
```

### **IDE配置建议**
在VSCode中配置：
```json
{
  "typescript.tsdk": "node_modules/typescript/lib",
  "typescript.enablePromptUseWorkspaceTsdk": true
}
```

### **验证镜像配置**
```bash
npm config get registry
time npm install typescript --registry=https://registry.npmmirror.com
```

通过以上步骤，可以在各操作系统上安装和管理TypeScript的多个版本，并利用国内镜像加速安装过程。



## C#



---

### **一、Windows 11**

#### **1. 安装最新.NET SDK**

```powershell
# 使用微软官方安装脚本（国内镜像加速）
irm https://dot.net/v1/dotnet-install.ps1 -Proxy 'http://mirrors.cloud.tencent.com' | iex
```

#### **2. 多版本管理**

```powershell
# 查看已安装版本
dotnet --list-sdks

# 安装指定版本（如7.0.400）
dotnet-install.ps1 -Channel 7.0 -Runtime dotnet -InstallDir "$env:LocalAppData\Microsoft\dotnet"

# 全局版本切换（修改系统PATH顺序）
$env:PATH = "C:\Users\[用户名]\AppData\Local\Microsoft\dotnet\;" + $env:PATH
```

#### **3. NuGet镜像配置**

```powershell
# 创建NuGet配置文件
New-Item -Path ~\.nuget\NuGet -ItemType Directory -Force
@"
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <packageSources>
    <add key="TencentCloud" value="https://mirrors.cloud.tencent.com/nuget/" />
  </packageSources>
</configuration>
"@ | Out-File -FilePath ~\.nuget\NuGet\NuGet.Config
```

---

### **二、macOS**

#### **1. 安装最新.NET SDK**

```bash
# 使用Homebrew（配置清华镜像）
echo 'export HOMEBREW_API_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/api"' >> ~/.zshrc
echo 'export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles"' >> ~/.zshrc
source ~/.zshrc

brew install --cask dotnet-sdk
```

#### **2. 多版本管理**

```bash
# 安装多个版本
brew install --cask dotnet-sdk6 dotnet-sdk7

# 查看可用版本
ls /usr/local/share/dotnet/sdk/

# 使用global.json指定版本
dotnet new globaljson --sdk-version 7.0.400
```

---

### **三、RHEL 9/AlmaLinux/Rocky Linux**

#### **1. 安装最新.NET SDK**

```bash
# 配置微软仓库（国内镜像加速）
sudo rpm -Uvh https://mirrors.tuna.tsinghua.edu.cn/dotnet/linux/rhel/9/prod.repo

# 安装.NET 8 SDK
sudo dnf install dotnet-sdk-8.0
```

#### **2. 多版本管理**

```bash
# 安装多版本
sudo dnf install dotnet-sdk-7.0 dotnet-sdk-6.0

# 使用符号链接切换版本
sudo ln -sf /usr/share/dotnet/dotnet /usr/bin/dotnet7
sudo ln -sf /usr/share/dotnet/dotnet /usr/bin/dotnet8

# 验证版本
dotnet8 --version
```

---

### **四、Ubuntu 24.04/Ubuntu Server**

#### **1. 安装最新.NET SDK**

```bash
# 配置清华镜像源
wget https://mirrors.tuna.tsinghua.edu.cn/dotnet/ubuntu/dotnet-8.list -O /etc/apt/sources.list.d/dotnet-8.list
sudo apt update

# 安装SDK
sudo apt install dotnet-sdk-8.0
```

#### **2. 多版本管理**

```bash
# 添加多个版本仓库
wget https://mirrors.tuna.tsinghua.edu.cn/dotnet/ubuntu/dotnet-7.list -O /etc/apt/sources.list.d/dotnet-7.list
sudo apt update

# 安装其他版本
sudo apt install dotnet-sdk-7.0

# 使用update-alternatives管理
sudo update-alternatives --install /usr/bin/dotnet dotnet /usr/share/dotnet/dotnet 100
```

---

### **五、Alpine Linux**

#### **1. 安装最新.NET SDK**

```bash
# 配置阿里云镜像
echo "http://mirrors.aliyun.com/alpine/latest-stable/main" > /etc/apk/repositories
echo "http://mirrors.aliyun.com/alpine/latest-stable/community" >> /etc/apk/repositories

# 安装.NET依赖
apk add icu-libs krb5-libs libgcc libintl libssl1.1 libstdc++ zlib

# 下载并安装.NET（手动选择版本）
wget https://mirrors.tuna.tsinghua.edu.cn/dotnet/linux/alpine/x64/dotnet-sdk-8.0.300-linux-musl-x64.tar.gz
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-8.0.300-linux-musl-x64.tar.gz -C $HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

---

### **六、通用配置**

#### **1. 项目级版本控制**

```bash
# 创建global.json文件
dotnet new globaljson --sdk-version 7.0.400 --force

# 文件内容示例：
{
  "sdk": {
    "version": "7.0.400",
    "rollForward": "latestFeature"
  }
}
```

#### **2. CI/CD优化配置**

```bash
# Docker多阶段构建示例
FROM mcr.mirrors.ustc.edu.cn/dotnet/sdk:8.0 AS build
COPY . .
RUN dotnet publish -c Release -o out

FROM mcr.mirrors.ustc.edu.cn/dotnet/aspnet:8.0
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "MyApp.dll"]
```

---

### **七、验证与调试**

```bash
# 检查SDK和运行时版本
dotnet --info

# 输出示例：
.NET SDK:
 Version:           8.0.300
 Commit:            abcdef01234
Runtime Environment:
 OS Name:     alpine
 OS Version:  3.19
```

---

### **八、注意事项**

1. **架构兼容性**：  

   - ARM设备需使用`arm64`架构包（如苹果M系列芯片）  
   - Alpine需选择`musl`版本包  

2. **安全更新**：  

   ```bash
   # Ubuntu自动更新检查
   sudo unattended-upgrade --dry-run
   ```

3. **企业级支持**：  

   - RHEL系推荐使用`Red Hat Software Collections (RHSCL)`  

   - 长期支持版本（LTS）选择：  

     ```bash
     sudo dnf module install dotnet-7.0-eol
     ```

通过以上步骤，可在各主流操作系统上搭建灵活且高效的C#开发环境，并适配国内网络环境。生产环境建议结合Docker容器化部署方案。



## Erlang

### **Windows 11**
#### **使用预编译二进制文件**
1. 访问 [Erlang官网](https://www.erlang.org/downloads) 下载最新Windows安装程序。
2. 安装时选择国内镜像服务器以加速下载。

#### **使用Scoop包管理器**
```powershell
scoop bucket add versions
scoop install erlang
```

### **macOS**
#### **使用Homebrew**
```bash
brew install erlang
```

#### **配置国内镜像**
```bash
echo 'export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles"' >> ~/.zshrc
source ~/.zshrc
```

### **RHEL/AlmaLinux/Rocky Linux**
#### **使用EPEL仓库**
```bash
sudo dnf install epel-release
sudo dnf install erlang
```

#### **配置国内镜像**
```bash
sudo sed -e 's|^mirrorlist=|#mirrorlist=|g' \
         -e 's|^#baseurl=http://download.fedoraproject.org/pub|baseurl=https://mirrors.tuna.tsinghua.edu.cn|g' \
         -i /etc/yum.repos.d/epel*
sudo dnf clean all
sudo dnf makecache
```

### **Ubuntu 24.04/Server**
#### **使用APT仓库**
```bash
wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb
sudo dpkg -i erlang-solutions_2.0_all.deb
sudo apt update
sudo apt install erlang
```

#### **配置国内镜像**
```bash
sudo sed -i 's|https://packages.erlang-solutions.com|https://mirrors.tuna.tsinghua.edu.cn/erlang|g' /etc/apt/sources.list.d/erlang-solutions.list
sudo apt update
```

### **Alpine Linux**
#### **使用APK包管理器**
```bash
apk add erlang
```

#### **配置国内镜像**
```bash
echo "http://mirrors.aliyun.com/alpine/latest-stable/main" > /etc/apk/repositories
echo "http://mirrors.aliyun.com/alpine/latest-stable/community" >> /etc/apk/repositories
apk update
```

### **多版本管理**
#### **使用Kerl工具**
```bash
# 安装Kerl
curl -O https://raw.githubusercontent.com/kerl/kerl/master/kerl
chmod a+x kerl
sudo mv kerl /usr/local/bin

# 构建指定版本
kerl build 25.3.2.6 25.3.2.6
kerl install 25.3.2.6 /path/to/erlang-25.3.2.6

# 激活版本
. /path/to/erlang-25.3.2.6/activate
```

### **通用配置**
#### **验证安装**
```bash
erl -version
```

#### **配置国内Hex镜像（包管理）**
```bash
# 配置Hex镜像
mix local.hex --if-missing --force
mix hex.config mirror_url https://hexpm.upyun.com
```

通过以上步骤，可以在各操作系统上安装和管理Erlang的多个版本，并利用国内镜像加速安装过程。



## PHP

### **Windows 11**
#### **使用XAMPP或WampServer**
1. 下载并安装[XAMPP](https://www.apachefriends.org/zh_cn/index.html)或[WampServer](http://www.wampserver.com/)，它们包含PHP的最新版本。

#### **手动安装PHP**
1. 访问 [PHP官网](https://windows.php.net/download/) 下载最新版本。
2. 配置环境变量，将PHP安装目录添加到PATH。

### **macOS**
#### **使用Homebrew**
```bash
brew install php
```

#### **配置国内镜像**
```bash
echo 'export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles"' >> ~/.zshrc
source ~/.zshrc
```

### **RHEL/AlmaLinux/Rocky Linux**
#### **使用Remi仓库**
```bash
sudo dnf install https://mirrors.tuna.tsinghua.edu.cn/remi/enterprise/remi-release-9.rpm
sudo dnf module enable php:remi-8.3
sudo dnf install php
```

#### **配置镜像**
```bash
sudo sed -i 's|baseurl=http://rpms.remirepo.net|baseurl=https://mirrors.tuna.tsinghua.edu.cn/remi|g' /etc/yum.repos.d/remi*.repo
sudo dnf clean all
sudo dnf makecache
```

### **Ubuntu 24.04/Server**
#### **使用Ondřej Surý的PPA**
```bash
sudo apt install software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt install php8.3
```

#### **配置国内镜像**
```bash
sudo sed -i 's|http://ppa.launchpad.net|https://launchpad.proxy.ustclug.org|g' /etc/apt/sources.list.d/ondrej-ubuntu-php-*.list
sudo apt update
```

### **Alpine Linux**
#### **使用APK包管理器**
```bash
apk add php83
```

#### **配置国内镜像**
```bash
echo "http://mirrors.aliyun.com/alpine/latest-stable/main" > /etc/apk/repositories
echo "http://mirrors.aliyun.com/alpine/latest-stable/community" >> /etc/apk/repositories
apk update
```

### **多版本管理**
#### **使用update-alternatives（Ubuntu/Debian）**
```bash
sudo update-alternatives --install /usr/bin/php php /usr/bin/php8.3 100
sudo update-alternatives --install /usr/bin/php php /usr/bin/php8.2 90
sudo update-alternatives --config php
```

#### **使用Remi仓库（RHEL系）**
```bash
sudo dnf module reset php
sudo dnf module enable php:remi-8.2
sudo dnf install php
```

### **配置PHP.ini**
```bash
sudo sed -i 's|;date.timezone =|date.timezone = Asia/Shanghai|g' /etc/php/8.3/php.ini
```

### **验证安装**
```bash
php -v
```

### **使用Docker多版本**
```dockerfile
FROM php:8.3-apache
COPY . /var/www/html
```

通过以上步骤，可以在各操作系统上安装和管理PHP的多个版本，并利用国内镜像加速安装过程。

## Ruby

以下是在各平台安装最新版Ruby、配置国内镜像及多版本管理的详细指南：

---

### **一、Windows 11**
#### 1. 安装最新Ruby
- **推荐方式**：使用RubyInstaller
  1. 下载最新版：[RubyInstaller](https://rubyinstaller.org/)
  2. 安装时勾选 **Add Ruby to PATH** 和 **MSYS2 Development Toolchain**

#### 2. 配置国内镜像
```bash
gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
```

#### 3. 多版本管理
- 使用 `ruby-installer` 或 `uru` 工具
```bash
# 安装uru
gem install uru
uru ls           # 列出已安装版本
uru 3.3.0        # 切换版本
```

---

### **二、macOS**
#### 1. 安装最新Ruby
```bash
brew install rbenv ruby-build
rbenv install 3.3.0   # 替换为最新版本号
rbenv global 3.3.0
```

#### 2. 配置国内镜像
```bash
echo "gem: --source=https://gems.ruby-china.com/" >> ~/.gemrc
```

#### 3. 多版本管理
```bash
rbenv install 3.2.0   # 安装其他版本
rbenv versions        # 查看所有版本
rbenv local 3.2.0     # 设置当前目录使用指定版本
```

---

### **三、RHEL/AlmaLinux/Rocky Linux**
#### 1. 安装最新Ruby
```bash
sudo dnf install git curl gcc make zlib-devel openssl-devel
curl -sSL https://rvm.io/mpapis.asc | gpg2 --import -
curl -sSL https://rvm.io/pkuczynski.asc | gpg2 --import -
curl -sSL https://get.rvm.io | bash -s stable
source ~/.rvm/scripts/rvm
rvm install ruby-3.3.0
```

#### 2. 配置国内镜像
```bash
bundle config mirror.https://rubygems.org https://gems.ruby-china.com
```

#### 3. 多版本管理
```bash
rvm install 3.2.0    # 安装其他版本
rvm use 3.2.0        # 切换版本
rvm list             # 查看已安装版本
```

---

### **四、Ubuntu 24.04/Ubuntu Server**
#### 1. 安装最新Ruby
```bash
sudo apt update
sudo apt install -y git curl autoconf bison build-essential libssl-dev libyaml-dev libreadline-dev zlib1g-dev libncurses5-dev libffi-dev libgdbm-dev
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/HEAD/bin/rbenv-installer | bash
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source ~/.bashrc
rbenv install 3.3.0
rbenv global 3.3.0
```

#### 2. 配置国内镜像
```bash
gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
```

#### 3. 多版本管理
```bash
rbenv install 3.2.0
rbenv local 3.2.0   # 项目级版本切换
```

---

### **五、Alpine Linux**
#### 1. 安装最新Ruby
```bash
sudo apk add git curl build-base libffi-dev openssl-dev readline-dev zlib-dev
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
cd ~/.rbenv && src/configure && make -C src
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.profile
echo 'eval "$(rbenv init -)"' >> ~/.profile
source ~/.profile
rbenv install 3.3.0
```

#### 2. 配置镜像
```bash
echo "gem: --source=https://gems.ruby-china.com/" >> ~/.gemrc
```

---

### **六、Docker 环境**
#### 1. 基于官方Ruby镜像
```Dockerfile
FROM ruby:3.3.0-alpine
RUN gem sources --add https://gems.ruby-china.com/ --remove https://rubygems.org/
```

#### 2. 自定义基础镜像（Ubuntu）
```Dockerfile
FROM ubuntu:24.04
RUN apt update && apt install -y rbenv ruby-build
ENV PATH="/root/.rbenv/bin:$PATH"
RUN rbenv install 3.3.0 && rbenv global 3.3.0
RUN gem sources --add https://gems.ruby-china.com/
```

---

### **七、通用多版本管理**
推荐工具：
- **rbenv**：轻量级，适合所有平台
- **RVM**：功能更丰富，但依赖较多

```bash
# 使用rbenv
rbenv install --list      # 查看可安装版本
rbenv install 3.2.0       # 安装旧版本
rbenv global 3.3.0        # 全局默认版本
rbenv local 3.2.0         # 项目级版本
```

---

### **总结**
1. **镜像加速**：统一替换 `https://gems.ruby-china.com`
2. **多版本管理**：优先使用 `rbenv` 或 `RVM`
3. **依赖安装**：所有系统均需安装编译工具链（如 `gcc`、`make`）
4. **Docker最佳实践**：优先使用官方镜像并添加镜像配置





