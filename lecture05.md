# 第五回課題
1. 組み込みサーバーでのRailsアプリケーション動作確認
2. UnicornでのRailsアプリケーション動作確認
3. Nginxの単体動作確認
4. NginxととUnicornを組み合わせてのRailsアプリケーションの動作確認
5. ELB(ALB)の追加
6. S3の追加
7. 構成図

### 1. 組み込みサーバーでのRailsアプリケーション動作確認
![組み込みサーバーでのRailsアプリケーション動作確認](/image/lecture05_image/lecture05_1.png)  
### 2. UnicornでのRailsアプリケーション動作確認  
+ Gemfile編集  　　
```
$ cd raisetech-live8-sample-app
$ vim Gemfile　　
# Use Unicorn as the app serverと追加
```

+ Unicornのインストール    
```
# Unicorn をインストール
$ bundle install  
```
+ UnicornでのRailsアプリケーション動作確認  
```
# unicorn.rbにlisten:3000追加
```  
 ![UnicornでのRailsアプリケーション動作確認](/image/lecture05_image/lecture05_2.png)

+ curlを使ってUnicornの動作確認  
```
$ curl --unix-socket /home/ec2-user/raisetech-live8-sample-app/unicorn.sock localhost
```  
![curl](/image/lecture05_image/lecture05_3.png)
### 3. Nginxの単体動作確認  
+ Nginxのインストール  
```
# amazon linux extrasでNginxをインストール
$ sudo amazon-linux-extras install nginx1

# Nginx起動
$ sudo systemctl start nginx

# nginx起動確認
$ sudo systemctl status nginx
```  
![Nginxの単体動作](/image/lecture05_image/lecture05_4.png) 
### 4. NginxととUnicornを組み合わせてのRailsアプリケーションの動作確認   
+ NginxにUnicornを使用するよう設定  
```
# Nginxの設定ファイルを編集する
$ sudo vim /etc/nginx/nginx.conf
```
![/etc/nginx/nginx.conf](/image/lecture05_image/lecture05_5.png)   
![nginxとunicorn](/image/lecture05_image/lecture05_6.png)  
### 5. ELB(ALB)の追加 
![ELB(ALB)の追加](/image/lecture05_image/lecture05_7.png)  
+ ALBのDNSでRailsアプリケーションの動作確認    
![ALBのDNS名でRailsアプリケーションの動作確認](/image/lecture05_image/lecture05_8.png) 
### 6. S3の追加  
![S3の追加](/image/lecture05_image/lecture05_9.png)  
S3に写真を保存  
![S3に写真を保存](/image/lecture05_image/lecture05_10.png)  
### 7. 構成図  
![構成図](/image/lecture05_image/lecture05_11.png)