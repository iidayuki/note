# RaspberryPiでalexaを動かす
RaspberryPiにマイクとスピーカーを接続してAmazon Echoを再現  
事前にAmazon Developerのアカウントに登録し、デバイスとセキュリティプロファイルを作成する。  
アカウント登録の説明・製品登録は[ここに]( https://github.com/iidayuki/note/blob/master/AmazonDevepoler.md )

## movie


## Requirement
* Raspberry Pi 3 Model B
* TOSHIBA microSD 16GB
* Raspbian - NOOBS v2.8.1
* BU-Bauty USBマイク
* SONY製 スピーカー

## Installation
* 1.RaspberyPiの起動まで
　まずはじめにフォーマットしたmicroSDカードにNOOBSファイルの中身をコピーし、RaspberryPiで起動する。  
　作業を楽にするためにVNCを設定 
  ~~Raspbianのセットアップは[ここに](  )~~
  
* 2.[alexa-avs-sample-app](https://github.com/alexa/alexa-avs-sample-app)をクローン 

      cd ~/Desktop/
      git clone https://github.com/alexa/alexa-avs-sample-app.git

* 3.製品情報**ProductID**、**ClientID**、**ClientSecret** を記入

      cd ~/Desktop/alexa-avs-sample-app
      vim automated_install.sh

* 4.インストールスクリプトを実行

      cd ~/Desktop/alexa-avs-sample-app
      . automated_install.sh
      
   * いくつかの簡単な質問に答える　　
   * 基本y(yes)で答える
   * 言語は**ja-JP** を選択
   * 音声の出力は**3.5mm jack** を選択
    
* 5.Webサービス、サンプルアプリケーション、Wake wordエンジンの実行
　ターミナルを3つ起動し、以下の順に実行  
  
    * 5-1
      承認のためにWebサービスを実行　　
      
          cd ~/Desktop/alexa-avs-sample-app/samples  
          cd companionService && npm start
   
    * 5-2
      AVS(Alexa Voice Service)と通信するサンプルアプリケーションの実行
      
          cd ~/Desktop/alexa-avs-sample-app/samples  
          cd javaclient && mvn exec:exec
      
       * デバイスの登録
       　![223](https://user-images.githubusercontent.com/27679709/43039315-95a27ae8-8d65-11e8-9dde-5927d78c1275.png)
         「はい」をクリック
       
       * [詳細設定] -> [localhostにアクセスする(安全ではありません)]をクリック
         ![225](https://user-images.githubusercontent.com/27679709/43039336-28246e9e-8d66-11e8-9ae0-51a99bab3ed5.png)
         ![226](https://user-images.githubusercontent.com/27679709/43039339-2ff2b37e-8d66-11e8-9890-37ca28c69c0e.png)
       
       * ログイン
         ![227](https://user-images.githubusercontent.com/27679709/43039341-37511bb0-8d66-11e8-9db4-074a5fbfa0ea.png)

       * デバイストークンが準備されていると表示されたら閉じ、「OK」ボタンをクリック
         ![228](https://user-images.githubusercontent.com/27679709/43039342-446afc58-8d66-11e8-83a5-a6c89aedaa5e.png)
         ![224](https://user-images.githubusercontent.com/27679709/43039343-49df12fa-8d66-11e8-9071-50b8711fa2f0.png)
         
    
    * 5-3
      "Alexa"というフレーズで起動させるために次のWake Wordエンジンのどちらかを実行
      
      * Sensory wake wordエンジンを使う場合
        
            cd ~/Desktop/alexa-avs-sample-app/samples  
            cd wakeWordAgent/src && ./wakeWordAgent -e sensory  
            
      * KITT.AI's wake wordエンジンを使う場合
      
            cd ~/Desktop/alexa-avs-sample-app/samples
            cd wakeWordAgent/src && ./wakeWordAgent -e kitt_ai  
            
       以下に使用可能なWake Wordエンジンの詳細
       * [Sensory]( https://github.com/Sensory/alexa-rpi )
       * [KATT.AI]( https://github.com/Kitt-AI/snowboy ) 
   
   これでハンズフリーのAVSプロトタイプが完成
    
## Usage
   目覚めの言葉「Alexa」を使うだけで、Alexaと話すことができる。
   例えば

   「Alexa」と言ってから、ビープ音を待つ。時間は？

   「Alexa」と言ってから、ビープ音を待つ。千葉の天気はどうですか？

   必要に応じて、目を覚ました単語を使用せずに、「聞き取り」ボタンをクリックでも起動可能。クリックを解除した後、「リッスン」ボタンを一度クリックし、話し始める前にオーディオキューを待つ。オーディオキューを聞くには、2〜3秒かかる場合がある。
  


