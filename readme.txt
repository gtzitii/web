前后端联调
1准备前后端资源：
    前端需要准备的文件：npm run build后生成的dist文件，nginx的配置文件nginx.conf
    后端需要准备的文件：maven package后生成的jar包
2创建项目目录，比如web：
    在web中创建两个文件夹，一个命名为frontend，一个命名为backend
        在frontend中，创建nginx文件夹，用于docker容器的数据卷挂载：
            在nginx中：
                拷贝nginx.conf，并且修改里面的端口和代理
                创建html文件夹，把前面准备好的前端dist文件中的所有内容拷贝到html目录下
        在backend中：
            拷贝jar包
            创建Dockerfile文件，并在该文件中写好构建后端镜像的代码
    在web中创建docker-compose.yml文件，并在其中写好部署脚本
3web文件内容写好后把web上传到github，执行以下代码：
    git add .
    git commit -m "web"
    git push
4在阿里云上先设置好ssh，方便克隆github仓库
    ssh-keygen -t ed25519 -C "zitaozhu1214@gmail.com"#注：填写github注册的邮箱
    私钥地址：~/.ssh/id_ed25519
    公钥地址：~/.ssh/id_ed25519.pub
    复制公钥，在github -> Settings -> SSH and GPG keys -> SSH keys中添加密钥
5拉取仓库资源并部署
    git clone git@github.com:gtzitii/web.git
    cd web
    docker compose up -d
    docker ps #查看容器是否成功启动
6等待10s左右，通过浏览器看是否能够访问
    