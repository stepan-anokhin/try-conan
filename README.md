# Example Conan Project


## Install Conan

See official docs [here](https://docs.conan.io/en/latest/installation.html).

Create python virtual environment
```shell
python3 -m venv $(pwd)/.venv
source .venv/bin/activate
```

Install Conan:
```shell
pip install conan
```

## Create project

See official docs [here](https://docs.conan.io/en/latest/getting_started.html).


Create a md5 calculator program depending on [Poco](https://pocoproject.org/):
```cpp
 #include "Poco/MD5Engine.h"
 #include "Poco/DigestStream.h"

 #include <iostream>

 int main(int argc, char** argv){
     Poco::MD5Engine md5;
     Poco::DigestOutputStream ds(md5);
     ds << "abcdefghijklmnopqrstuvwxyz";
     ds.close();
     std::cout << Poco::DigestEngine::digestToHex(md5.digest()) << std::endl;
     return 0;
 }
 ```

Search for poco package:
```shell
conan search poco --remote=conancenter
```
```
WARN: Remotes registry file missing, creating default one in /home/stepan/.conan/remotes.json
Existing package recipes:

poco/1.8.1
poco/1.9.3
poco/1.9.4
poco/1.10.0
poco/1.10.1
```

Inspect `poco/1.10.1` package: 
```shell
conan inspect poco/1.10.1
```
```
name: poco
version: 1.10.1
url: https://github.com/conan-io/conan-center-index
homepage: https://pocoproject.org
license: BSL-1.0
author: None
description: Modern, powerful open source C++ class libraries for building network- and internet-based applications that run on desktop, server, mobile and embedded systems.
topics: ('conan', 'poco', 'building', 'networking', 'server', 'mobile', 'embedded')
generators: ('cmake', 'cmake_find_package')
exports: None
exports_sources: ('CMakeLists.txt', 'patches/**')
short_paths: False
apply_env: True
build_policy: None
revision_mode: hash
settings: ('os', 'arch', 'compiler', 'build_type')
options:
    enable_apacheconnector: [True, False]
    enable_cppparser: [True, False]
    enable_crypto: [True, False]
    enable_data: [True, False]
    enable_data_mysql: [True, False]
    enable_data_odbc: [True, False]
    enable_data_postgresql: [True, False]
    enable_data_sqlite: [True, False]
    enable_encodings: [True, False]
    enable_json: [True, False]
    enable_jwt: [True, False]
    enable_mongodb: [True, False]
    enable_net: [True, False]
    enable_netssl: [True, False]
    enable_netssl_win: [True, False]
    enable_pagecompiler: [True, False]
    enable_pagecompiler_file2page: [True, False]
    enable_pdf: [True, False]
    enable_pocodoc: [True, False]
    enable_redis: [True, False]
    enable_sevenzip: [True, False]
    enable_util: [True, False]
    enable_xml: [True, False]
    enable_zip: [True, False]
    fPIC: [True, False]
    shared: [True, False]
default_options:
    enable_apacheconnector: False
    enable_cppparser: False
    enable_crypto: True
    enable_data: True
    enable_data_mysql: True
    enable_data_odbc: False
    enable_data_postgresql: True
    enable_data_sqlite: True
    enable_encodings: True
    enable_json: True
    enable_jwt: True
    enable_mongodb: True
    enable_net: True
    enable_netssl: True
    enable_netssl_win: True
    enable_pagecompiler: False
    enable_pagecompiler_file2page: False
    enable_pdf: False
    enable_pocodoc: False
    enable_redis: True
    enable_sevenzip: False
    enable_util: True
    enable_xml: True
    enable_zip: True
    fPIC: True
    shared: False
deprecated: None
```
