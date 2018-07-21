# RaspberryPiでalexaを動かす
RaspberryPiにマイクとスピーカーを接続してAmazon Echoを再現
事前にAmazon Developerのアカウントに登録し、デバイスとセキュリティプロファイルを作成する。
~~その説明は[ここに](  )~~

## movie


## Requirement
* Raspberry Pi 3 Model B
* TOSHIBA microSWD 16GB
* Raspbian - NOOBS v2.8.1
* BU-Bauty USBマイク
* SONY製 スピーカー

## Installation
* 1.RaspberyPiの起動まで
　まずはじめにフォーマットしたmicroSDカードにNOOBSファイルの中身をコピーし、RaspberryPiで起動する。  
　作業を楽にするためにVNCを設定 
  ~~Raspbianのセットアップは[ここに](  )~~
  
* 2.インストールスクリプトと設定ファイルのダウンロード  

      cd ~/Desktop/
      git clone https://github.com/alexa/alexa-avs-sample-app.git

* 3.製品情報**ProductID**、**ClientID**、**ClientSecret** を記入

      cd ~/Desktop/alexa-avs-sample-app
      vim automated_install.sh

* 4.インストールスクリプトを実行

      cd ~/Desktop/alexa-avs-sample-app
      . automated_install.sh
      
   以下の質問に答える
   
   
   
    
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
  


