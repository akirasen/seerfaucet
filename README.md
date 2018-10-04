# 安装水龙头

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
cd seerfaucet
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
修改完成后使用`Control` + `o` `enter`保存修改，`Control` + `x`退出。

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
  password:                #数据库登录密码，根据安装mysql时的填写，千万注意:和密码之间应有空格，否则之后创建数据库时会报错
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

修改完成后使用`Control` + `o` `enter`保存修改，`Control` + `x`退出。

### 配置密码种子文件secrets.yml
(ruby on rails用到的密码种子配置文件)
生成三段随机密码种子
```linux
rake secret
```
例如：
```linux
root@ubuntu-s-1vcpu-1gb-sfo2-01:~/seerfaucet# rake secret
7e39b462ad366a4bb3560281541274d04846dc0ec62c76ead47a66911e3e30015c8969ddade0d923720b5a593683ff96f9ada58f3f9c5c7cdc6a9fe85d846664
root@ubuntu-s-1vcpu-1gb-sfo2-01:~/seerfaucet# rake secret
e3812e46b183a2d04e2a29e30faea5ea33114cbf18128ae5dd4c5a6828d27d9d366bad658e987cbff5faed2ec0e3a6a4a1ed0c2d2910b00f1a7461663eb4e7fc
root@ubuntu-s-1vcpu-1gb-sfo2-01:~/seerfaucet# rake secret
89fdf6eb4c5a13abfde3ee1b6503d61e5e8e8b2ee3745dc125620a1f1e8b384ee9fb6f0957cb419621742807ca5a11185e63467f58cca23dd5da9f83af0317d5
```
然后将密码种子填入secrets.yml中，替换掉`abcdefg123456 `
```linux
nano config/secrets.yml
```
```nano
development:                                          
  secret_key_base: abcdefg123456                      
                                                      
test:                                                 
  secret_key_base: abcdefg123456                      
                                                      
# Do not keep production secrets in the repository,   
# instead read values from the environment.           
production:                                           
  secret_key_base: 89fdf6eb4c5a13abfde3ee1b6503d61e5e8e8b2ee3745dc125620a1f1e8b384ee9fb6f0957cb419621742807ca5a11185e63467f58cca23dd5da9f83af0317d5//示例  
```

修改完成后使用`Control` + `o` `enter`保存修改，`Control` + `x`退出。

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

水龙头连接钱包正常的显示：
```
root@ubuntu-s-1vcpu-1gb-sfo2-01:~/seerfaucet# rails s -b 0.0.0.0
=> Booting WEBrick
=> Rails 4.2.4 application starting in development on http://0.0.0.0:3000
=> Run `rails server -h` for more startup options
=> Ctrl-C to shutdown server
Starting graphene websocket communication event-loop 'ws://127.0.0.1:9991'
Established connection to 'ws://127.0.0.1:9991'
[2018-10-04 09:29:00] INFO  WEBrick 1.3.1
[2018-10-04 09:29:00] INFO  ruby 2.2.3 (2015-08-18) [x86_64-linux]
[2018-10-04 09:29:00] INFO  WEBrick::HTTPServer#start: pid=21639 port=3000
```

完成后隐藏此screen:

`Control` + `a` `d`

## 使用钱包连接此水龙头

之后在ubuntu或mac上运行一个SEER-UI dev环境，将此水龙头设为默认水龙头。

详细操作步骤参考：https://github.com/seer-project/Seer-UI

### 简明SEER-UI部署流程

将以下命令复制到终端中执行即可安装 NVM。
```linux
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.30.2/install.sh | bash
nvm install v6
nvm use v6
```
Node 安装完成后，获取项目的源代码：
```linux
screen -S Seer-ui
git clone https://github.com/seer-project/Seer-ui.git
cd Seer-ui
```
修改钱包的默认水龙头：
```linux
nano app/api/apiConfig.js
```
修改apiConfig.js第49行的代码：
```js
DEFAULT_FAUCET: "https://www.seerapi.com",
```
修改为你的水龙头ip和端口，例如：
```js
DEFAULT_FAUCET: "http://206.189.169.23:3000",
```
在启动之前，需要先安装 npm 软件包：
```linux
npm install
```
所有软件包安装好后，可以使用以下命令启动开发服务器：
```linux
npm start
```
编译完成后，即可通过浏览器访问 localhost:9080 或 127.0.0.1:9080 打开钱包。

## 了解注册流程

以上步骤中作为测试，仅修改了水龙头地址，默认SEER-UI依然使用SEER主网网络，若要将SEER-UI改为测试网络，还需要修改接入点和chain-id，此处不深入介绍。

### 查看水龙头

在使用了此水龙头的SEER-UI注册新账号`"fffff"`成功后，可以在测试网络区块浏览器 http://123.206.78.97/explorer/blocks 观察到如下信息：

```
okok 注册了账户 fffff
```
使用
```linux
screen -r faucet
```
恢复screen faucet，在screen faucet可以观察到如下信息：
```linux
Started OPTIONS "/api/v1/accounts" for 112.44.141.143 at 2018-10-04 09:34:36 +0000
Cannot render console from 112.44.141.143! Allowed networks: 127.0.0.1, ::1, 127.0.0.0/127.255.255.255
  ActiveRecord::SchemaMigration Load (0.4ms)  SELECT `schema_migrations`.* FROM `schema_migrations`
Processing by Api::BaseController#option as */*
  Parameters: {"path"=>"v1/accounts"}
  Rendered text template (0.0ms)
Completed 200 OK in 16ms (Views: 6.0ms | ActiveRecord: 0.0ms)


Started POST "/api/v1/accounts" for 112.44.141.143 at 2018-10-04 09:34:37 +0000
Cannot render console from 112.44.141.143! Allowed networks: 127.0.0.1, ::1, 127.0.0.0/127.255.255.255
Processing by Api::V1::AccountsController#create as JSON
  Parameters: {"account"=>{"name"=>"fffff", "owner_key"=>"SEER6f7kZTPvA7g2aRZaFbBjDbNYLy3XT4m71VPdRMnGeZKczpFMms", "active_key"=>"SEER7Ha3fpfBqt6zW1SsMjUHjguoGMPSDs3HS6KQWGWUX4agSFDkU8", "memo_key"=>"SEER7Ha3fpfBqt6zW1SsMjUHjguoGMPSDs3HS6KQWGWUX4agSFDkU8", "refcode"=>nil, "referrer"=>nil}}
   (0.2ms)  BEGIN
  SeerAccount Exists (1.3ms)  SELECT  1 AS one FROM `seer_accounts` WHERE `seer_accounts`.`remote_ip` = BINARY '112.44.141.143' AND (created_at > '2018-10-04 09:29:37') LIMIT 1
---- Registering account: 'fffff' SEER7Ha3fpfBqt6zW1SsMjUHjguoGMPSDs3HS6KQWGWUX4agSFDkU8/SEER6f7kZTPvA7g2aRZaFbBjDbNYLy3XT4m71VPdRMnGeZKczpFMms referrer: 
call: [0, "get_account", ["fffff"]]
call: [0, "get_account", ["fffff"]]
Websocket RPC Error: {"code"=>1, "message"=>"Assert Exception: rec && rec->name == account_name_or_id: ", "data"=>{"code"=>10, "name"=>"assert_exception", "message"=>"Assert Exception", "stack"=>[{"context"=>{"level"=>"error", "file"=>"wallet.cpp", "line"=>601, "method"=>"get_account", "hostname"=>"", "thread_name"=>"th_a", "timestamp"=>"2018-10-04T09:34:37"}, "format"=>"rec && rec->name == account_name_or_id: ", "data"=>{}}, {"context"=>{"level"=>"warn", "file"=>"websocket_api.cpp", "line"=>122, "method"=>"on_message", "hostname"=>"", "thread_name"=>"th_a", "timestamp"=>"2018-10-04T09:34:37"}, "format"=>"", "data"=>{"call.method"=>"call", "call.params"=>[0, "get_account", ["fffff"]]}}]}}
Websocket RPC Error: {"code"=>1, "message"=>"Assert Exception: rec && rec->name == account_name_or_id: ", "data"=>{"code"=>10, "name"=>"assert_exception", "message"=>"Assert Exception", "stack"=>[{"context"=>{"level"=>"error", "file"=>"wallet.cpp", "line"=>601, "method"=>"get_account", "hostname"=>"", "thread_name"=>"th_a", "timestamp"=>"2018-10-04T09:34:37"}, "format"=>"rec && rec->name == account_name_or_id: ", "data"=>{}}, {"context"=>{"level"=>"warn", "file"=>"websocket_api.cpp", "line"=>122, "method"=>"on_message", "hostname"=>"", "thread_name"=>"th_a", "timestamp"=>"2018-10-04T09:34:37"}, "format"=>"", "data"=>{"call.method"=>"call", "call.params"=>[0, "get_account", ["fffff"]]}}]}}
call: [0, "register_account", ["fffff", "SEER7Ha3fpfBqt6zW1SsMjUHjguoGMPSDs3HS6KQWGWUX4agSFDkU8", "SEER6f7kZTPvA7g2aRZaFbBjDbNYLy3XT4m71VPdRMnGeZKczpFMms", "okok", "okok", 0, true]]
call: [0, "register_account", ["fffff", "SEER7Ha3fpfBqt6zW1SsMjUHjguoGMPSDs3HS6KQWGWUX4agSFDkU8", "SEER6f7kZTPvA7g2aRZaFbBjDbNYLy3XT4m71VPdRMnGeZKczpFMms", "okok", "okok", 0, true]]
{"ref_block_num"=>61162, "ref_block_prefix"=>2022767456, "expiration"=>"2018-10-04T09:35:06", "operations"=>[[4, {"fee"=>{"amount"=>514257, "asset_id"=>"1.3.0"}, "registrar"=>"1.2.105", "referrer"=>"1.2.105", "referrer_percent"=>0, "name"=>"fffff", "owner"=>{"weight_threshold"=>1, "account_auths"=>[], "key_auths"=>[["SEER7Ha3fpfBqt6zW1SsMjUHjguoGMPSDs3HS6KQWGWUX4agSFDkU8", 1]], "address_auths"=>[]}, "active"=>{"weight_threshold"=>1, "account_auths"=>[], "key_auths"=>[["SEER6f7kZTPvA7g2aRZaFbBjDbNYLy3XT4m71VPdRMnGeZKczpFMms", 1]], "address_auths"=>[]}, "options"=>{"memo_key"=>"SEER6f7kZTPvA7g2aRZaFbBjDbNYLy3XT4m71VPdRMnGeZKczpFMms", "voting_account"=>"1.2.5", "num_committee"=>0, "num_authenticator"=>0, "num_supervisor"=>0, "votes"=>[], "extensions"=>[]}, "extensions"=>{}}]], "extensions"=>[], "signatures"=>["1f19bf7e127acb07d8b56e183ba4839d53be35bb7aae233e407db6cc373bbc8f5c6e54fcf4b6252abe7a5a3be3a4b5724b3e4a32ae2595e5b9f22a7190453aac05"]}
  SQL (0.5ms)  INSERT INTO `seer_accounts` (`name`, `owner_key`, `active_key`, `memo_key`, `remote_ip`, `created_at`, `updated_at`) VALUES ('fffff', 'SEER6f7kZTPvA7g2aRZaFbBjDbNYLy3XT4m71VPdRMnGeZKczpFMms', 'SEER7Ha3fpfBqt6zW1SsMjUHjguoGMPSDs3HS6KQWGWUX4agSFDkU8', 'SEER7Ha3fpfBqt6zW1SsMjUHjguoGMPSDs3HS6KQWGWUX4agSFDkU8', '112.44.141.143', '2018-10-04 09:34:37', '2018-10-04 09:34:37')
   (1.4ms)  COMMIT
  Rendered api/v1/accounts/show.json.jbuilder (2.7ms)
Completed 201 Created in 1364ms (Views: 6.6ms | ActiveRecord: 4.6ms)
```
完成后隐藏此screen:

`Control` + `a` `d`

而使用
```linux
screen -r seer
```
恢复screen seer，在screen seer可以观察到如下信息：

```cmd
2078541ms th_a       websocket_api.cpp:109         on_message           ] API call execution time limit exceeded. method: call params: [0,"register_account",["fffff","SEER7Ha3fpfBqt6zW1SsMjUHjguoGMPSDs3HS6KQWGWUX4agSFDkU8","SEER6f7kZTPvA7g2aRZaFbBjDbNYLy3XT4m71VPdRMnGeZKczpFMms","okok","okok",0,true]] time: 1046857
```
完成后隐藏此screen:

`Control` + `a` `d`

所以水龙头的作用是把SEER-UI或其它前端发起的包含用户名、公钥的注册请求，判断是否符合规则，然后将信息存入本地数据库后，调用命令行钱包来注册账号。

## 水龙头的更多功能

### 注册后自动向用户转账或发行资产

您可以修改水龙头注册文件，让水龙头注册新用户后，自动向该账户转入一定数额的token，让用户体验DAPP功能。

编辑注册文件：

```linux
nano seerfaucet/app/services/account_registrator.rb
```
第60-61行使用ruby的`#`注释掉的两行代码，分别是向新注册用户账户转入50万SEER测试币和新发行1000万BTC测试币给该用户。
```ruby
GrapheneCli.instance.exec('issue_asset', [account_name, '10000000', 'BTC', 'Welcome to SEER. https://Seer.best', true])
GrapheneCli.instance.exec('transfer', [registrar_account, account_name, '500000', 'SEER', 'Welcome to SEERTALK. https://forum.seerchain.org', true])

```
去掉`#`，并改为您要使用的资产类型即可，若要使用资产发行功能，命令行钱包内需要有资产发行人的active key。

修改后，需要切换到screen faucet，`Control` + `c`关闭水龙头，然后`rails s -b 0.0.0.0`重启。

效果如下：

注册新账号`dddddd`成功后，测试网络区块浏览器观察效果如下：

```
okok 将 500,000 SEER 转账给 dddddd
else 将 10,000,000.0000 BTC 发行给 dddddd
okok 注册了账户 dddddd
```

### 导出注册用户列表

每次注册新用户，水龙头程序都会在mysql数据库中自动记录下注册用户的信息，笔者暂时没有测试出通过邮件接收注册信息的方法，但可以从数据库中直接将注册信息导出为根目录下的excel表格。方法如下：

```linux
mysql -p seer_faucet_dev -u root -e "select * from seer_accounts" > ~/seer.xls
```
`ls`就会发现根目录下多了一个`seer.xls`文件，在本地电脑的终端里输入：

```
scp root@服务器ip:seer.xls ~/seer.xls
```
即可将此文件下载到本地。

