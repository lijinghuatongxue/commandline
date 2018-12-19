#### YUM 命令 

基于 RPM 的系统使用了包管理器, 你可以用这些命令获取到有关已安装包或者其它工具的有用信息。

| 命令                                 | 描述                                                   |
| ------------------------------------ | ------------------------------------------------------ |
| yum update                           | 使用 YUM 更新所有的 RPM 包，也会显示出哪些已经过时了。 |
| yum update httpd                     | 更新单独的包，在此例中是 HTTPD (Apache)。              |
| yum install package                  | 使用 YUM 安装一个包。                                  |
| yum --exclude=package kernel* update | 在使用 YUM 时将一个包排除在外不更新。                  |
| yum remove package                   | 使用 YUM 删除包。                                      |
| yum erase package                    | 使用 YUM 删除包。                                      |
| yum list package                     | 列出有关 yum 包的信息。                                |
| yum provides httpd                   | 显示一个包的用途，例如： Apache HTTPD Server。         |
| yum info httpd                       | 显示包信息，架构，版本等信息。                         |
| yum localinstall blah.rpm            | 使用 YUM 来安装本地 RPM， 从资源库进行安装。           |
| yum deplist package                  | 显示包的提供方信息。                                   |
| yum list installed                   | 列出所有已安装的包。                                   |
| yum grouplist                        | 显示所有的 YUM 分组。                                  |
| yum groupinstall 'Development Tools' | 安装 YUM 分组。                                        |

