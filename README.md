# configfilereader

#### 介绍
配置文件读取库，用于读取配置文件中的配置信息

#### 软件架构
软件架构说明


#### 安装教程

可直接使用

#### 使用说明

配置文件：
```
# the configure file
server_ip=127.0.0.1    # the server ip
server_port=9080   # the server port

示例程序：
#include "app_config.h"
#include <iostream>

int main()
{
	AppConfig* config = AppConfig::get_instance();
	if (config->initialize("config.cfg", "=", "#"))
	{
		bool ret = config->is_config_file_exists();
		std::cout << "The config file [config.cfg] exists:" << ret << std::endl;

		ret = config->read_and_parse();
		std::cout << "The config file [config.cfg] read and parse:" << ret << std::endl;

		std::string serverIP = AppConfig::get_instance()->get_by_key("server_ip", "127.0.0.1");
		std::string serverPort = AppConfig::get_instance()->get_by_key("server_port", "8080");
		std::cout << "server ip: " << serverIP << " port: " << serverPort << std::endl;

		std::cout << "the configs list: \n" << *config << std::endl;
	}

	system("pause");

    return 0;
}

