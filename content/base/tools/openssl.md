+++
title = "openssl"
date = 2025-03-10T07:22:49+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++



## 是什么

​	OpenSSL 是一个 C 语言编写的开源软件库，包含对 `SSL` 和 `TLS` 协议的开源实现。它不仅是一个库，还提供命令行工具，用于执行各种加密任务，如生成密钥、证书管理和数据加密。它的广泛使用得益于其开源性质和跨平台支持（包括 Linux、macOS、Windows 等）。

​	OpenSSL 是现代互联网安全的基石之一，无论是开发者还是系统管理员，都可能直接或间接与之打交道。如果你需要处理加密、证书或网络安全，几乎必然会遇到它。

​	OpenSSL之所以能成为互联网安全通信的重要组成部分，很大程度上得益于其基于C语言的实现，这不仅保证了库的性能和稳定性，还促进了其在不同平台上的移植和使用。

​	尽管OpenSSL的核心是用C语言编写的，但它也可以通过其他编程语言的绑定或接口（如Python、Perl、Ruby等）来使用，这样就允许更多的开发者群体能够利用OpenSSL的功能，即使他们主要使用的不是C语言。

## 作用和功能（按最常用的顺序给出）

### 实现 SSL/TLS 协议以确保安全通信

​	这是 OpenSSL 最核心和最常见的角色，特别是在 web 服务器中，用于实现 HTTPS 协议。研究表明，大多数互联网服务器（包括绝大多数 HTTPS 网站）依赖 OpenSSL 来保护通信免受窃听，并验证通信双方的身份。例如，web 浏览器和服务器之间的安全连接通常通过 OpenSSL 的库功能实现，确保数据机密性和完整性。这一功能在现代互联网中至关重要，尤其是在电子商务和在线银行等需要高安全性的场景中。

### 密钥和证书管理

​	OpenSSL 的第二个主要作用是生成和管理加密密钥和证书，这是设置安全通信的基础。管理员和开发者常用 OpenSSL 的命令行工具来生成 RSA 私钥、创建证书签名请求（CSR）、生成自签名证书或验证证书详情。例如，web 服务器管理员可能使用 `openssl genrsa` 生成私钥，然后用 `openssl req` 创建 CSR，这个 CSR 随后提交给证书颁发机构（CA）以申请证书。这一步骤在部署安全网站或 VPN 时尤为常见，是确保通信安全的关键部分。

### 提供通用加密功能

​	OpenSSL 还支持各种通用加密操作，包括对称加密（如 AES）、非对称加密（如 RSA）、哈希函数（如 SHA-256）和数字签名。这些功能可用于加密文件、验证数据完整性或在应用程序中集成加密逻辑。例如，开发者可能使用 `openssl enc` 命令对敏感数据进行 AES-256 加密，或用 `openssl dgst` 计算文件的哈希值以确保未被篡改。虽然这一功能在各种安全应用中都有用，但其使用频率通常低于前两项，因为它更多地服务于特定场景而非普遍需求。

## 安装、配置、更新、卸载（不同操作系统）

### Linux

- 安装：OpenSSL 通常预装在大多数 Linux 发行版上。如果未安装，可通过包管理器安装：
  - Ubuntu/Debian：`sudo apt-get install openssl`
  - Red Hat/CentOS：`sudo yum install openssl`
  - Fedora：`sudo dnf install openssl`
- **配置**：配置取决于使用场景，例如为 Apache 或 NGINX 配置 SSL/TLS。
- 更新：通过包管理器更新：
  - Ubuntu/Debian：`sudo apt-get update && sudo apt-get upgrade`
  - Red Hat/CentOS：`sudo yum update`
  - Fedora：`sudo dnf update`
- 卸载：不建议卸载，因为它是系统库，但若必要：
  - Ubuntu/Debian：`sudo apt-get remove openssl`
  - Red Hat/CentOS：`sudo yum remove openssl`
  - Fedora：`sudo dnf remove openssl`

### macOS

- 安装：macOS 默认安装较旧版本，可通过 Homebrew 获取最新版本：

  - 安装 Homebrew：参考 [brew.sh](https://brew.sh)
  - 安装 OpenSSL：`brew install openssl`

- **配置**：安装后通过 openssl 命令使用，系统范围可用则需链接：`brew link --force openssl`

  > ​	研究表明，当通过 Homebrew 安装 OpenSSL 时，它被标记为 keg-only，这意味着安装后不会自动将二进制文件链接到 Homebrew 的前缀目录（如 /usr/local/bin 或 /opt/homebrew/bin），这些目录通常在用户的 PATH 环境变量中。
  >
  > - **证据**：根据 [Understand homebrew and keg-only dependencies - Stack Overflow](https://stackoverflow.com/questions/17015285/understand-homebrew-and-keg-only-dependencies) 的讨论，keg-only 意味着软件安装在 /usr/local/Cellar 下，但不链接到 /usr/local/bin 等位置。因此，其他依赖它的软件需要通过指定完整路径使用。
  >
  > - **具体案例**：安装 OpenSSL 后，其二进制文件位于 /usr/local/Cellar/openssl/[版本]/bin/openssl，用户若想使用，必须手动运行 /usr/local/Cellar/openssl/[版本]/bin/openssl，而不能直接输入 openssl。
  >
  >   因此，在未链接前，OpenSSL 不能直接从终端的任何目录运行 openssl 命令，只能通过指定完整路径使用，这相当于只能在安装目录下间接使用。
  >
  > ​	**链接的过程与必要性**
  >
  > ​	为了使 openssl 命令系统范围可用，即从任何目录直接运行，需要运行 brew link --force openssl。这会创建符号链接，将 /usr/local/Cellar/openssl/[版本]/bin/openssl 链接到 /usr/local/bin/openssl。
  >
  > - **证据**：根据 [Tips and Tricks — Homebrew Documentation](https://docs.brew.sh/Tips-N'-Tricks) 的内容，brew link 用于将公式安装的文件符号链接到 Homebrew 的前缀目录。对于 keg-only 公式，如 OpenSSL，需要使用 --force 选项，因为默认情况下 Homebrew 拒绝链接以避免冲突。
  > - **原因分析**：macOS 系统可能已有自己的 SSL/TLS 实现（如 LibreSSL），根据 [Homebrew keg only install of openssl - cet-is - Fermilab Redmine](https://cdcvs.fnal.gov/redmine/projects/cet-is/wiki/Homebrew_keg_only_install_of_openssl) 的内容，OpenSSL 被标记为 keg-only 是因为 Apple 已弃用 OpenSSL，优先使用自己的库，以避免版本冲突。
  >
  > 因此，未链接前，OpenSSL 确实只能通过完整路径使用，链接后才能实现系统范围可用。

- **更新**：`brew update && brew upgrade openssl`

- **卸载**：通过 Homebrew 卸载：`brew unlink openssl` 和 `brew remove openssl`

### Windows

- 安装：Windows 未预装 OpenSSL，可从官网下载或使用第三方安装程序如 

  Win64 OpenSSL，可以下载地址可以参考这里：[https://wiki.openssl.org/index.php/Binaries](https://wiki.openssl.org/index.php/Binaries)：

  - 下载安装程序并按提示安装。

- **配置**：安装后需设置 PATH 环境变量，包含 OpenSSL bin 目录（如 C:\OpenSSL-Win64\bin）。

- **更新**：下载最新版本重新安装，并更新 PATH。

- **卸载**：通过控制面板卸载或运行安装包提供的卸载程序。

## 示例（按最常用的顺序给出）

### 示例 1：生成私钥和自签名证书



### 示例 2：加密和解密文件



### 示例 3：使用 SHA-256 哈希验证文件完整性



## 注意事项（使用时的注意事项）



