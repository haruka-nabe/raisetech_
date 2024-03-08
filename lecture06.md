# 第六回課題  
1. CloudTrailイベント一覧  
2. CloudWatch    
3. 利用料見積もり  
4. 先月のEC2使用料



1． ClodTrailイベント一覧　　
 ![CloudTrailイベント一覧](/image/lecture06_image/lecture06_1.png)

+ イベント名：Startinstances　　
+ 書かれていること
　 ユーザー名、イベントソース、イベント名 
![イベント名](/image/lecture06_image/lecture06_2.png)　　

2．CloudWatch  
+ アラーム作成  
![アラーム作成](/image/lecture06_image/lecture06_3.png) 

+ Rails使えるとき(Nginx、Unicorn起動時)　　

![RailsOK](/image/lecture06_image/lecture06_4.png)  
![RailsOK_mail](/image/lecture06_image/lecture06_5.png)  

+ Rails使えないとき(Nginx、Unicorn停止時)  
![Railsunhealthy](/image/lecture06_image/lecture06_6.png)  
![Railsunhealthy_mail](/image/lecture06_image/lecture06_7.png)  

3.　利用料の見積もり　
+ 第五回で使用したソースの見積もりを行った。

[pricing calculatorを用いた見積もり](https://calculator.aws/#/estimate?id=ec3326a84c449df5177a12bb614f9d33b28aeadc)　　

　　
4.　先月のEC2使用料 　　

 ![先月のEC2使用料](/image/lecture06_image/lecture06_8.png)
 
 + 無料利用枠で収まっていない。→使わないソースは削除、EC2の起動・停止時間を自動化することでコストカットを行った。EventBridgeルールで、月～金の9:00AMに、インスタンスを起動するSystems Manager Automation ドキュメントを設定。
EventBridgeルールで、月～金の21:00PMに、インスタンスを停止するSSM Automation ドキュメントを設定。