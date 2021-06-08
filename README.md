# Google-Smartphone-Decimeter-Challenge
Google-Smartphone-Decimeter-Challengeコンペのリポジトリ

## Dataset

## Basics
**Overview(DeepL)**

不意にポットホールなどの道路障害物にぶつかったことはありませんか？また、ナビゲーションアプリで、より正確な位置情報や車線レベルの精度が得られたらと思ったことはありませんか？これらの機能やその他の新しい機能は、スマートフォンの測位サービスによって実現されています。機械学習と高精度GNSSアルゴリズムにより、この精度が向上し、何十億人ものAndroid携帯電話ユーザーに、よりきめ細かな測位体験を提供できるようになると期待されています。



全地球測位衛星システム（GNSS）は、生の信号を提供し、GPSチップセットはそれを使って位置を計算します。現在の携帯電話では、3〜5メートルの位置精度しか得られません。これは多くの場合、便利ではありますが、"ビビり "の原因となります。多くのユースケースでは、その結果は、信頼できるほど細かくも安定してもいません。

Android GPSチームが主催するこのコンテストは、ION GNSS+ 2021 Conferenceで発表されます。彼らは、スマートフォンのGNSS測位精度の研究を進め、人々が身の回りの世界をよりよくナビゲートできるようにすることを目指しています。

このコンペティションでは、ホストチームが所有するAndroid携帯電話から収集したデータを使用して、可能であれば10cm、さらにはcm単位の分解能で位置を計算します。また、正確なグラウンドトゥルース、生のGPS測定値、近隣のGPSステーションからのアシスタンスデータを利用して、応募作品のトレーニングとテストを行います。

成功すれば、より正確な位置情報を得ることができ、より細かい人間の行動の地理空間情報と、より細かい粒度のモバイルインターネットとの橋渡しをすることができます。モバイルユーザーは、より良い車線レベルの座標を得て、ロケーションベースのゲームの経験を強化し、交通安全上の問題の位置をより具体的に把握することができます。さらには、行きたい場所に簡単に行けるようになったことに気づくかもしれません。


**data(deepL)**   

このチャレンジでは、GPS衛星からの信号、加速度計の測定値、ジャイロスコープの測定値など、携帯電話の位置を決定するのに役立つさまざまな機器からのデータを提供します。

この課題では、車線レベルのマッピングなどの後処理に重点を置いて設計されているため、将来的にはルート上のデータを利用して、可能な限り正確な位置を生成することができます。また、複数の機種で構成される路線も多いため、隣接する機種の情報を利用して推定を行うこともできます。一般的なGNSS測位アルゴリズムの開発を促進するため、携帯電話内のGPSチップセットの位置情報は提供されません。これは、携帯電話のモデルなどによって異なるメーカー独自のアルゴリズムに基づいているためです。

データ収集プロセスの詳細については、本稿をご参照ください。このデータセット／課題に基づいて作品を発表する場合は、コンペティションルールに基づいて適切に引用してください。


### train.csv column infomation
[Dataページ](https://www.kaggle.com/c/google-smartphone-decimeter-challenge/data)を参照（baseline_locations_[train/test].csv自体の特徴量の説明は無い。他ファイルの説明を参照）

|name|Explanation|
|----|----|
|collectionName|各collectionのID,親の親フォルダ名を指している|
|phoneName|機種名、親フォルダ名|
|millisSinceGpsEpoch|GPSエポックからの整数ミリ秒|
|latDeg,lngDeg|参照GNSS受信機によって推定されたWGS８４緯度、経度|
|heightAboveWgs84EllipsoidM|参照GNSS受信機によって推定されたWGS楕円体上の高さ|
|phone|collection名＋機種名（？）|

Files（deepL）

[train]/[drive_id]/[phone_name]/ground_truth.csv - トレーニングセットでのみ提供。予想されるタイムスタンプでの参照場所


[train/test]/[drive_id]/[phone_name]/supplemental/[phone_name][.20o/.21o/.nmea] - GPSコミュニティで使用されている他のフォーマットのgnssログと同等のデータです。


baseline_locations_[train/test].csv - シンプルなアプローチで生成された推定座標。

# Log
### 20210527
- 初submit-nb001
### 20210530
- Kaggle日記初作成
  - ~~READMEファイルに画像を貼る方法が分からない…→メンターさんに質問~~
  
  　→ 画像を上げてリンクを貼れば良いっぽいが何故か画像がアップロードできない
  - 打ち消し線は”~~"で囲えば引ける
  - まずはDataについて整理（[このNotebook](https://www.kaggle.com/c/google-smartphone-decimeter-challenge/discussion/241039)を参照）
  - GitHub上にフォルダ作成する方法（https://qiita.com/tommy_aka_jps/items/b2ae85cbeab77e12a925）
### 20210601
- 画像を上げてリンクを貼れば良いっぽいが何故か画像がアップロードできない
　
 　→addまでは出来たがなぜかmasterブランチが勝手に出来てしまう問題が発生
   
### 20210602
- データの内容をザッと説明するNotebook（A quick explanation of the data：https://www.kaggle.com/c/google-smartphone-decimeter-challenge/discussion/241039）
を読んだ。付随するNotebookも読んだ、前にも一応読んでるけど。（①[Getting oriented if you're new to GPS](https://www.kaggle.com/c/google-smartphone-decimeter-challenge/discussion/238590),②[Methodology behind the baseline location estimates](https://www.kaggle.com/c/google-smartphone-decimeter-challenge/discussion/238583)）

  - ①は最初にどのデータを使えばいいのか教えてくれている、②はbaselineデータの取得方法（あんま分かってなくても良さそう）

- これ書いてるとEnterで勝手に文章がコピペされるの何なんだ…

- とりあえず上位のNotebookをsubmitしたいけど、どれを使えばいいんだ？てかそもそも公開Notebook以外って見れるの？

### 20210603
- Notebook読んでも内容まとめないと忘れることに気づく
  -各データのcolumnsの意味をまとめて書いておこう
- リザードンの人のNotebook分かりやすいからこれ読み込んでみるか

### 20210606
- 体調悪い…
- とりあえずこのノートブックを読んでみた（https://www.kaggle.com/c/google-smartphone-decimeter-challenge/discussion/244283）

1.データセットを理解する
  
2.機械学習で既にいいスコアが出ているので、他の技術を検討すべし
  
3.外れ値を修正する
4.データ平滑化を試す（カルマンフィルタなど）
5.データの後処理を行う
6.ハイパーパラメーターチューニングを行う
7.gnssや派生ファイルも使ってみる
### 20210607
- ハーバーサイン距離（？）や半何とか関数のノートブック探して何とか見つけた
### 20210608
- ハーバーサイン距離のわかりやすい説明を見つけた（https://paulownia.hatenablog.com/entry/2018/12/16/212203）
