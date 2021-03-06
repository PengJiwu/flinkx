# FTP写入插件（ftpwriter）

## 1. 配置样例

```
{
    "job": {
        "setting": {
            "speed": {
                 "channel": 2
            },
            "errorLimit": {
                "record": 0,
                "percentage": 0.02
            }
        },
        "content": [
            {
              "reader": {
                "parameter": {
                  "password": "abc123",
                  "columnTypes": [
                    "java.lang.String",
                    "java.lang.String"
                  ],
                  "column": [
                    "col1",
                    "col2"
                  ],
                  "connection": [
                    {
                      "jdbcUrl": [
                        "jdbc:mysql://172.16.8.104:3306/test?charset=utf8"
                      ],
                      "table": [
                        "tb1"
                      ]
                    }
                  ],
                  "splitPk": "col1",
                  "username": "dtstack"
                },
                "name": "mysqlreader"
              },
               "writer": {
                    "name": "ftpwriter",
                    "parameter": {
                    	"protocol": "sftp",
                      	"host": "node03",
                      	"port": 22,
                      	"username": "mysftp",
                      	"password": "oh1986mygod",
                      	"writeMode": "overwrite",
                      	"path": "/upload/xxx",
                        "fieldDelimiter": ",",
                        "column": [
                            {
                                "name": "col1",
                                "type": "string"
                            },
                            {
                                "name": "col2",
                                "type": "string"
                            }
                        ]
                    }
                }
            }
        ]
    }
}

```

## 2. 参数说明

* **protocol**

	* 描述：ftp服务器协议，目前支持传输协议有ftp和sftp。 <br />
 
	* 必选：是 <br />
 
	* 默认值：无 <br />
	
* **host**

	* 描述：ftp服务器地址。 <br />
 		 
	* 必选：是 <br />
 
	* 默认值：无 <br />
	
* **port**

	* 描述：ftp服务器端口。 <br />
 
	* 必选：否 <br />
 
	* 默认值：若传输协议是sftp协议，默认值是22；若传输协议是标准ftp协议，默认值是21 <br />
	
	
* **username**

	* 描述：ftp服务器访问用户名。 <br />
 
	* 必选：是 <br />
 
	* 默认值：无 <br />

* **password**

	* 描述：ftp服务器访问密码。 <br />
 
	* 必选：是 <br />
 
	* 默认值：无 <br />

* **path**

	* 描述：FTP文件系统的路径信息，FtpWriter会写入Path目录下属多个文件。 <br />
			 
	* 必选：是 <br />
 
	* 默认值：无 <br />
 

* **writeMode**
 
 	* 描述：FtpWriter写入前数据清理处理模式： <br />
			 
		* overwrite，覆盖
		* append，追加
		
	* 必选：是 <br />
 
	* 默认值：无 <br />

* **fieldDelimiter**

	* 描述：读取的字段分隔符 <br />
 
	* 必选：否 <br />
 
	* 默认值：, <br />
 	
* **encoding**

	* 描述：读取文件的编码配置。<br />
 
 	* 必选：否 <br />
 
 	* 默认值：utf-8 <br />
 
