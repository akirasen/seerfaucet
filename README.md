# 安装

## 环境

此水龙头代码在石墨烯水龙头源码（https://github.com/cryptonomex/faucet ）上修改，指南示例在DigitalOcean ubuntu 16.04 服务器上测试正常。ubuntu 18.04、更高版本ruby，甚至相同配置下的vultr服务器均有各种报错，欢迎填坑。
此使用SEER测试网络，若有需要，请更换为主网。

## 在服务器运行一个SEER命令行钱包

新建一个screen，命名为seer。
```linux
screen -S seer
```
新建一个目录，命名为seer。
```linux
mkdir seer
```
下载最新版本SEER命令行钱包到seer目录，并重命名为seer.tar.gz
```linux
curl -Lo seer/seer.tar.gz https://github.com/seer-project/seer-core-package/releases/download/v0.04/seer-ubuntu-0.0.4.tar.gz
```
进入seer目录
```linux
cd seer
```
解压缩seer.tar.gz
```linux
tar xzvf seer.tar.gz
```
启动命令行钱包，此例中的chain-id为测试网络，通过任意命令行钱包输入info指令获取，默认为主网chain-id，-s参数为钱包连接的节点api，此处为测试网络公告api节点，-r参数为钱包暴露的websocket RPC端口，水龙头程序即是通过此端口控制命令行钱包进行操作， -H为钱包暴露的HTTP RPC端口，所有端口都可以自行修改。
```linux
./cli_wallet --chain-id="da68a9c5f2fd9ed48e626ea301db1c77505523884ba0dd409e779246c6ea26cf" -s ws://123.206.78.97:8002 -r 127.0.0.1:9991 -H 127.0.0.1:9992
```
以上指令可以复制以下命令粘贴至终端，一次性执行：

```linux
screen -S seer
mkdir seer
curl -Lo seer/seer.tar.gz https://github.com/seer-project/seer-core-package/releases/download/v0.04/seer-ubuntu-0.0.4.tar.gz
cd seer
tar xzvf seer.tar.gz
./cli_wallet --chain-id="da68a9c5f2fd9ed48e626ea301db1c77505523884ba0dd409e779246c6ea26cf" -s ws://123.206.78.97:8002 -r 127.0.0.1:9991 -H 127.0.0.1:9992
```

设置钱包解锁密码，123替换为你想设置的密码
```cmd
set_password 123
```
解锁钱包
```cmd
unlock 123
```
导入账号资金私钥
```cmd
import_key okok 5JkbV8aTaYRVaarTUJQ9Y56cr4QajxNFfCoQj6Q9JFL8XvUZ5CQ
import_key else 5KiSC6rRAEkTj72fg3G3zF8RHmCEgZw7aSXBjKqDfvY2XN1qvyd
```
以上指令可以复制以下命令粘贴至终端，一次性执行：
```cmd
set_password 123
unlock 123
import_key okok 5JkbV8aTaYRVaarTUJQ9Y56cr4QajxNFfCoQj6Q9JFL8XvUZ5CQ
import_key else 5KiSC6rRAEkTj72fg3G3zF8RHmCEgZw7aSXBjKqDfvY2XN1qvyd
```

钱包连接正常的显示：
```linux
mkdir seer
curl -Lo seer/seer.tar.gz https://github.com/seer-project/seer-core-package/releases/download/v0.04/seer-ubuntu-0.0.4.tar.gz
cd seer
tar xzvf seer.tar.gz
./cli_wallet --chain-id="da68a9c5f2fd9ed48e626ea301db1c77505523884ba0dd409e779246c6ea26cf" -s ws://123.206.78.97:8002 -r 127.0.0.1:9991 -H 127.0.0.1:9992
root@ubuntu-s-1vcpu-1gb-sfo2-01:~# mkdir seer
root@ubuntu-s-1vcpu-1gb-sfo2-01:~# curl -Lo seer/seer.tar.gz https://github.com/seer-project/seer-core-package/releases/download/v0.04/seer-ubuntu-0.0.4.tar.gz
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   615    0   615    0     0   1044      0 --:--:-- --:--:-- --:--:--  1045
100 13.7M  100 13.7M    0     0   904k      0  0:00:15  0:00:15 --:--:-- 2220k
root@ubuntu-s-1vcpu-1gb-sfo2-01:~# cd seer
root@ubuntu-s-1vcpu-1gb-sfo2-01:~/seer# tar xzvf seer.tar.gz
cli_wallet
witness_node
root@ubuntu-s-1vcpu-1gb-sfo2-01:~/seer# ./cli_wallet --chain-id="da68a9c5f2fd9ed48e626ea301db1c77505523884ba0dd409e779246c6ea26cf" -s ws://123.206.78.97:8002 -r 127.0.0.1:9991 -H 127.0.0.1:9992
Logging RPC to file: logs/rpc/rpc.log
3562294ms th_a       main.cpp:131                  main                 ] key_to_wif( committee_private_key ): 5KCBDTcyDqzsqehcb52tW5nU6pXife6V2rX9Yf7c3saYSzbDZ5W
3562295ms th_a       main.cpp:135                  main                 ] nathan_pub_key: SEER6MRyAjQq8ud7hVNYcfnVPJqcVpscN5So8BhtHuGYqET5GDW5CV
3562295ms th_a       main.cpp:136                  main                 ] key_to_wif( nathan_private_key ): 5KQwrPbwdL6PhXujxW37FSSQZ1JiwsST4cqQzDeyXtP79zkvFD3
Starting a new wallet with chain ID da68a9c5f2fd9ed48e626ea301db1c77505523884ba0dd409e779246c6ea26cf (from CLI)
3562296ms th_a       main.cpp:183                  main                 ] wdata.ws_server: ws://123.206.78.97:8002
3562921ms th_a       main.cpp:188                  main                 ] wdata.ws_user:  wdata.ws_password:  
Please use the set_password method to initialize a new wallet before continuing
3564395ms th_a       main.cpp:227                  main                 ] Listening for incoming RPC requests on 127.0.0.1:9991
3564396ms th_a       main.cpp:252                  main                 ] Listening for incoming HTTP RPC requests on 127.0.0.1:9992
new >>> set_password 123
set_password 123
null
locked >>> unlock 123
unlock 123
null
unlocked >>> import_key okok 5JkbV8aTaYRVaarTUJQ9Y56cr4QajxNFfCoQj6Q9JFL8XvUZ5CQ
import_key okok 5JkbV8aTaYRVaarTUJQ9Y56cr4QajxNFfCoQj6Q9JFL8XvUZ5CQ
3572083ms th_a       wallet.cpp:793                save_wallet_file     ] saving wallet to file wallet.json
3572084ms th_a       wallet.cpp:467                copy_wallet_file     ] backing up wallet wallet.json to after-import-key-1cd0784e.wallet
true
unlocked >>> import_key else 5KiSC6rRAEkTj72fg3G3zF8RHmCEgZw7aSXBjKqDfvY2XN1qvyd
import_key else 5KiSC6rRAEkTj72fg3G3zF8RHmCEgZw7aSXBjKqDfvY2XN1qvyd
3572941ms th_a       wallet.cpp:467                copy_wallet_file     ] backing up wallet wallet.json to before-import-key-1bece5d8.wallet
3573189ms th_a       wallet.cpp:793                save_wallet_file     ] saving wallet to file wallet.json
3573191ms th_a       wallet.cpp:467                copy_wallet_file     ] backing up wallet wallet.json to after-import-key-1bece5d8.wallet
true
unlocked >>> 
```

完成后隐藏此screen:

`Control` + `a` `d`

## 安装mysql和依赖环境
```linux
apt update
apt-get install -y mysql-server libmysqlclient-dev  libreadline-dev build-essential nodejs ruby-railties libssl-dev
```
在安装过程中会提示设置mysql的密码。

## 安装ruby环境
```linux
cd ~
git clone git://github.com/sstephenson/rbenv.git .rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL

git clone git://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
exec $SHELL

git clone https://github.com/sstephenson/rbenv-gem-rehash.git ~/.rbenv/plugins/rbenv-gem-rehash


rbenv install 2.2.3
rbenv global 2.2.3
gem install bundler
```
## 下载水龙头代码

```linux
git clone https://github.com/akirasen/seerfaucet
cd faucet
bundle
```
## 配置水龙头文件

### 水龙头访问配置faucet.yml

我们建议使用 nano 是因为它是一个经典的图形文本编辑器，只使用了方向键。

```linux
nano config/faucet.yml
```
配置文件介绍如下：
```nano
cli_wallet_connection: ws://127.0.0.1:9991   //钱包开放的websocketurl，cli_wallet-H参数对应  ./cli_wallet --chain-id="da68a9c5f2fd9ed48e626ea301db1c77505523884ba0dd409e779246c6ea26cf" -s ws://123.206.78.97:8002 -r 127.0.0.1:9991 -H 127.0.0.1:9992  
registrar_account: okok                    //提供注册的推荐人用户名，本例子为在SEER测试网络已创建且升级为会员的用户名okok
referrer_percent: 50       // 推荐人分成百分比                     
refcode_prefix: F01                                
                                                   
default_url: 127.0.0.1                       //水龙头对外访问的IP      
default_port: 3000                           //水龙头对外访问的端口
                                                   
exception_notification:                            //以下设置可以不用设置，应该是发送和接受注册及异常信息的邮件配置
  sender_address: faucet@example.com               
  exception_recipients: admin@example.com          
                                                   
smtp:                                              
  address: address                                 
  user_name: user                                  
  password: password 
```
### 数据库配置database.yml

```linux
nano config/database.yml
```

```nano
default: &default
  adapter: mysql2
  encoding: utf8
  pool: 5
  username: root           #数据库登录用户名                   
  password:                #数据库登录密码，根据安装mysql时的填写
  host: localhost          #数据库url          
                                     
development:
  <<: *default
  database: seer_faucet_dev

test:
  <<: *default
  database: seer_faucet_test

production:
  <<: *default
  database: seer_faucet

```
### 配置密码种子文件secrets.yml
(ruby on rails用到的密码种子配置文件)
生成三段随机密码种子
```linux
rake secret
```

然后将密码种子填入secrets.yml中，替换掉`abcdefg123456 `
```linux
development:                                          
  secret_key_base: abcdefg123456                      
                                                      
test:                                                 
  secret_key_base: abcdefg123456                      
                                                      
# Do not keep production secrets in the repository,   
# instead read values from the environment.           
production:                                           
  secret_key_base: abcdefg123456   
```
## 创建并初始化数据库

```linux
rake db:create; rake db:migrate; rake db:seed
RAILS_ENV=production bundle exec rake db:create db:schema:load
```
## 运行水龙头服务
新建一个screen，命名为faucet

```linux
screen -S faucet
```
启动水龙头服务

```linux
rails s -b 0.0.0.0
```

`-b`，bind之意。是让本机以外的主机，能够访问水龙头服务。

完成后隐藏此screen:

`Control` + `a` `d`


之后运行一个SEER-UI，将此水龙头设为默认水龙头
