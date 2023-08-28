# その他の参考情報

> **Note**
> 当文書は[Resources](https://github.com/chiphuyen/dmls-book/blob/main/resources.md)を日本語に翻訳したものです。


この文書は、本書で触れたトピックをさらに深掘りすることが目的です。本書には既に膨大な数のリンクや参考文献を掲載しているため、読者が重要なポイントを見落としてしまわないように掲載を見送った情報があります。

* [1章.機械学習システムの概要](#1章機械学習システムの概要)
* [2章.機械学習システム設計の概要](#2章機械学習システム設計の概要)
* [3章.データエンジニアリングの基礎知識](#3章データエンジニアリングの基礎知識)
    * [ストリーミングシステム](#ストリーミングシステム)
* [4章.訓練データ](#4章訓練データ)
* [5章.特徴エンジニアリング](#5章特徴エンジニアリング)
* [6章.モデル開発とオフライン評価](#6章モデル開発とオフライン評価)
    * [訓練、デバッグ、機械学習コードのテスト](#訓練デバッグ機械学習コードのテスト)
    * [モデルの評価](#モデルの評価)
* [7章.モデルのデプロイと予測サービス](#7章モデルのデプロイと予測サービス)
* [8章.データ分布のシフトと監視](#8章データ分布のシフトと監視)
* [9章.実現場での継続学習とテスト](#9章実現場での継続学習とテスト)
    * [文脈バンディット（Contextual bandits）](#文脈バンディット)
* [10章.MLOpsにおけるインフラとツール](#10章MLOpsにおけるインフラとツール)
* [11章.機械学習の人的側面](#11章機械学習の人的側面)

## 1章.機械学習システムの概要

機械学習システムの設計を学ぶには、ケーススタディを読んで実際のチームが様々なデプロイ要件や制約に対してどのように対処しているかを知ることが有益です。多くの企業（例を挙げると、Airbnb、Lyft、Uber、Netflixなど）が、素晴らしい技術ブログを立ち上げて、機械学習を活用してプロダクトやプロセスの改善に役立てたエピソードを公開しています。

1. [Using Machine Learning to Predict Value of Homes On Airbnb](https://medium.com/airbnb-engineering/using-machine-learning-to-predict-value-of-homes-on-airbnb-9272d3d4739d) (Robert Chang, Airbnb Engineering & Data Science, 2017)

詳細かつ洗練されたこのブログ記事の中でChangは、Airbnbが機械学習を使用して重要なビジネス指標であるAirbnb上の住宅の価値をいかに予測したかについて解説しています。この記事では、特徴エンジニアリング、モデルの選定、プロトタイピング、プロトタイプを実環境へ移行するまでのワークフロー全体が網羅されており、さらには、そこから得られた教訓や使用したツール、コードスニペットなども掲載されています。

2. [Using Machine Learning to Improve Streaming Quality at Netflix](https://medium.com/netflix-techblog/using-machine-learning-to-improve-streaming-quality-at-netflix-9651263ef09f) (Chaitanya Ekanadham, Netflix Technology Blog, 2018)

2018年時点でNetflixは全世界で1億1700万人以上のユーザーにストリーミングサービスを提供しており、その半数は米国外でのユーザーです。このブログ記事では、ネットワーク品質の予測、デバイスの異常の検出、予測をキャッシュするためのリソースの割り当てなど、直面する技術的な課題とその課題を克服する機械学習の活用方法について解説しています。

3. [150 Successful Machine Learning Models: 6 Lessons Learned at Booking.com](https://blog.kevinhu.me/2021/04/25/25-Paper-Reading-Booking.com-Experiences/bernardi2019.pdf) (Bernardi et al., KDD, 2019)

Booking.comは2019年には既に150個もの機械学習モデルを実稼働させています。これらのモデルは、ユーザーの旅行の好みや同行者数などの広範な予測問題や、ユーザーに表示する背景画像やレビューの最適化問題に取り組むものです。[こちら](https://blog.acolyer.org/2019/10/07/150-successful-machine-learning-models/)では、Adrian Colyerが得た6つの教訓について素晴らしいまとめを提供しています。

1. 機械学習モデルはビジネスに大きな価値を提供する
2. モデルのパフォーマンスとビジネスのパフォーマンスは異なる
3. 解決したい問題を明確にせよ
4. 予測を提供するレイテンシーは重要である
5. モデルの品質のフィードバックを迅速に得よ
6. ランダム化比較試験（randomized controlled trials）を用いてモデルのビジネス上の影響をテストせよ

4. [How we grew from 0 to 4 million women on our fashion app, with a vertical machine learning approach](https://medium.com/hackernoon/how-we-grew-from-0-to-4-million-women-on-our-fashion-app-with-a-vertical-machine-learning-approach-f8b7fc0a89d7) (Gabriel Aldamiz, HackerNoon, 2018)

Chicisimoはコーディネートのアドバイスを自動で提供できるようにしようと、機械学習を用いて人々のファッションの嗜好を定義しようとしました。このタスクには曖昧なところがあるため、問題の組み立て方とデータの収集方法が大きな課題となります。この両方の取り組みが記事の中で言及されています。さらに、すべてのコンシューマー向けアプリが直面するユーザーの繋ぎ止め（リテンション）の問題についても触れています。

5. [Machine Learning-Powered Search Ranking of Airbnb Experiences](https://medium.com/airbnb-engineering/machine-learning-powered-search-ranking-of-airbnb-experiences-110b4b1a0789) (Mihajlo Grbovic, Airbnb Engineering & Data Science, 2019)

この記事は、ランキングとレコメンドに関する問題の典型的な事例をステップバイステップで説明したものです。主なステップは、システム設計、パーソナライゼーション、オンラインスコアリング、そしてビジネスの視点の4つです。この記事では、どの特徴を使用するか、データをどのように集めてラベル付けするか、なぜ勾配ブースト決定木（Gradient Boosted Decision Tree）を採用したのか、どのテスト指標を利用するか、ランク付けする際の考慮事項、そしてどのようにデプロイしてA/Bテストを実施するかなどについて詳しく述べられています。また、この記事の特筆すべき点として、ユーザーごとに異なるランキングを提供するパーソナライゼーションについても採り上げている点が挙げられます。

6. [From shallow to deep learning in fraud](https://eng.lyft.com/from-shallow-to-deep-learning-in-fraud-9dafcbcef743) (Hao Yi Ong, Lyft Engineering, 2018)

不正検知（Fraud detection）は、産業界の機械学習のユースケースとしてもっとも古くからあるもののひとつです。この記事では、Lyftでの不正検知アルゴリズムの変遷について説明しています。初期の頃は、特徴エンジニアリングによるロジスティック回帰だけで多くの不正を検出できました。この手法はシンプルであるため、さまざまな特徴の重要性をチームが理解できました。しかしながら、不正の手口が巧妙になるにつれて、より高度なモデルが求められるようになりました。この記事では、モデルの複雑さと説明能力、そして効果とデプロイのしやすさとの間にあるトレードオフについて語っています。

7. [Space, Time and Groceries](https://tech.instacart.com/space-time-and-groceries-a315925acf3a) (Jeremy Stanley, Tech at Instacart, 2017)

Instacartは機械学習を使用して複数の買い物客にもっとも効率的にタスクを割り当てて最適な経路を見つけられるようにしています。この記事では、問題の定義、データの収集、アルゴリズムや評価指標の選択、さらに綺麗に可視化するチュートリアルに至るまでのシステム設計の全工程を詳細に説明しています。

8. [Creating a Modern OCR Pipeline Using Computer Vision and Deep Learning](https://blogs.dropbox.com/tech/2017/04/creating-a-modern-ocr-pipeline-using-computer-vision-and-deep-learning/) (Brad Neuberg, Dropbox Engineering, 2017)

文書をスキャンするだけのシンプルなアプリケーションでさえ、光学文字認識と単語検出の2つの独立したコンポーネントから構成されます。それぞれのコンポーネントに専用の製造パイプラインが必要となり、エンド・ツー・エンドのシステム（システム全体）としては、訓練やチューニングの手順がさらに必要です。また、この記事では、自前のデータアノテーションプラットフォームを構築するなどのデータの収集に関するチームの取り組みについても詳細に説明しています。

9. [Spotify’s Discover Weekly: How machine learning finds your new music](https://hackernoon.com/spotifys-discover-weekly-how-machine-learning-finds-your-new-music-19a41ab76efe) (Umesh .A Bhat, 2017)

Spotifyは、主に3種類のレコメンド用モデルを使用してDiscover Weeklyを作成しています。

* **協調フィルタリング**モデル... 元々はLast.fmが使用していたもので、あなたの行動や他の人々の行動を分析します。
* **自然言語処理**モデル（NLP）... テキストを分析します。
* **オーディオ**モデル... 生のオーディオトラックそのものを分析します。

10. [Smart Compose: Using Neural Networks to Help Write Emails](https://ai.googleblog.com/2018/05/smart-compose-using-neural-networks-to.html) (Yonghui Wu, Google AI Blog 2018)

“_Smart Composeはキーを入力するたびに予測を実行するので、ユーザーに遅延を感じさせることがないように、理想的には **100ミリ秒** 以内に応答しなければなりません。モデルの複雑さと推論の速さとの間でバランスを取ることが極めて重要な課題でした。_”

## 2章.機械学習システム設計の概要

* [Rules of Machine Learning](https://developers.google.com/machine-learning/guides/rules-of-ml) (Martin Zinkevich)
* [Things I wish we had known before we started our first Machine Learning project](https://medium.com/infinity-aka-aseem/things-we-wish-we-had-known-before-we-started-our-first-machine-learning-project-336d1d6f2184) (Aseem Bansal, towards-infinity 2018)
* [https://github.com/chiphuyen/machine-learning-systems-design](https://github.com/chiphuyen/machine-learning-systems-design): だいぶ前に書いたもので、本書に比べるとあまり整理されていません。
* [Deploying Machine Learning Models: A Checklist](https://twolodzko.github.io/ml-checklist) （機械学習システムの設計に関する簡単なチェックリスト）

## 3章.データエンジニアリングの基礎知識

* [A Beginner’s Guide to Data Engineering](https://medium.com/@rchang/a-beginners-guide-to-data-engineering-part-i-4227c5c457d7) (Robert Chang 2018)
* [Designing Data-Intensive Applications](https://learning.oreilly.com/library/view/designing-data-intensive-applications/9781491903063/) (Martin Kleppmann, O’Reilly, 2017)
* [Emerging Architectures for Modern Data Infrastructure](https://future.a16z.com/emerging-architectures-modern-data-infrastructure/) (Bornstein et al, a16z 2022) 
* [Reverse ETL — A Primer](https://medium.com/memory-leak/reverse-etl-a-primer-4e6694dcc7fb) (Astasia Myers 2021)
* [Uber’s Big Data Platform: 100+ Petabytes with Minute Latency](https://eng.uber.com/uber-big-data-platform/) (Reza Shiftehfar, Uber Engineering blog 2018)
* [How DoorDash is Scaling its Data Platform to Delight Customers and Meet our Growing Demand](https://doordash.engineering/2020/09/25/how-doordash-is-scaling-its-data-platform/) (Sudhir Tonse 2020)


### ストリーミングシステム

* [The Log: What every software engineer should know about real-time data's unifying abstraction](https://engineering.linkedin.com/distributed-systems/log-what-every-software-engineer-should-know-about-real-time-datas-unifying) (Jay Kreps, LinkedIn / Confluent, 2013): Jayはこの[ツイート](https://twitter.com/jaykreps/status/1408159236794765314) で言及していますが、彼がこのブログを執筆したのは、ストリーミングにどれだけの関心があるかを見極めて、それ次第で彼のチームで新しい事業を興すかどうかを判断するためでした。このブログの反響は大きく、彼のチームはLinkedInからスピンアウトしてConfluentを設立しました。
* [The Many Meanings of Event-Driven Architecture](https://www.youtube.com/watch?v=STKCRSUsyP0) (Martin Fowler, GOTO 2017): Martin Fowlerは偉大な講演者です。彼の講演によりイベント駆動型アーキテクチャーの複雑さの大部分が明確になりました。
* [Stream Processing Hard Problems – Part 1: Killing Lambda](https://engineering.linkedin.com/blog/2016/06/stream-processing-hard-problems-part-1-killing-lambda) (Kartik Paramasivam, LinkedIn Engineering 2016)
* [Open Problems in Stream Processing: A Call To Action](https://docs.google.com/presentation/d/1YtTEnOax5MDA8DazDa1ad-sP4zzM58KQK4HNAcxoONA/edit#slide=id.p) (Tyler Akidau, DEBS 2019): TylerはかつてGoogleでDataflowのリーダーを務めていましたが、2020年1月にSnowflakeに参画し、ストリーミングチームを発足しました。彼のこのセッションでは、ストリーミング処理における主な課題について解説しています。
* [The Four Innovation Phases of Netflix's Trillions Scale Real-time Data Infrastructure](https://zhenzhongxu.com/the-four-innovation-phases-of-netflixs-trillions-scale-real-time-data-infrastructure-2370938d7f01) (Zhenzhong Xu, 2022): Netflixがどのようにバッチシステムからストリーミングシステムに移行したかについて述べています。

## 4章.訓練データ

* [Rejection sampling](https://en.wikipedia.org/wiki/Rejection_sampling)
* [The MIDAS Touch: Mixed Data Sampling Regression Models](https://escholarship.org/uc/item/9mf223rs) (Ghysels et al., 2004)
* [An Overview of Weak Supervision](https://www.snorkel.org/blog/weak-supervision) (Ratner et al., 2018) 

## 5章.特徴エンジニアリング

* [Interpretable Machine Learning](https://christophm.github.io/interpretable-ml-book/) (Christoph Molnar, 2022): 説明能力（解釈可能性）についてかなり詳しく解説しています。

## 6章.モデル開発とオフライン評価

### 訓練、デバッグ、機械学習コードのテスト

* [How to unit test machine learning code](https://medium.com/@keeper6928/how-to-unit-test-machine-learning-code-57cf6fd81765) (Chase Roberts, 2017)
* [A Recipe for Training Neural Networks](http://karpathy.github.io/2019/04/25/recipe/) (Andrej Karpathy, 2019)
* [Top 6 errors novice machine learning engineers make](https://medium.com/ai%C2%B3-theory-practice-business/top-6-errors-novice-machine-learning-engineers-make-e82273d394db) (Christopher Dossman, AI³ | Theory, Practice, Business 2017)
* [Testing and Debugging in Machine Learning](https://developers.google.com/machine-learning/testing-debugging) course (Google)
* [What did you wish you knew before deploying your first ML model?](https://twitter.com/chipro/status/1348265019012743169)（私がTwitterで問いかけたところ、興味深いリプライが寄せられました。）
* [Techniques for Training Large Neural Networks](https://openai.com/blog/techniques-for-training-large-neural-networks/) (OpenAI 2022) 
* [A survey of model compression and acceleration for deep neural networks](https://arxiv.org/abs/1710.09282) (Cheng et al., IEEE Signal Processing Magazine 2017)
* [Towards Federated Learning at Scale: System Design](https://arxiv.org/abs/1902.01046) (Bonawitz et al, 2019)


### モデルの評価

* [Effective testing for machine learning systems](https://www.jeremyjordan.me/testing-ml/) (Jeremy Jordan, 2020)
* [On Calibration of Modern Neural Networks](https://arxiv.org/abs/1706.04599) (Guo et al., 2017)
* [Calibration for Netflix recommendation systems](https://dl.acm.org/doi/10.1145/3240323.3240372) (Harald Steck, 2018)
* [Beyond Accuracy: Behavioral Testing of NLP Models with CheckList](https://aclanthology.org/2020.acl-main.442/) (Ribeiro et al., ACL 2020)
* [TextBugger: Generating Adversarial Text Against Real-world Applications](https://arxiv.org/abs/1812.05271) (Li et al., 2018) 
* [Uncertainty Sets for Image Classifiers using Conformal Prediction](https://arxiv.org/abs/2009.14193) (Angelopoulos et al., 2020)


## 7章.モデルのデプロイと予測サービス


## 8章.データ分布のシフトと監視

* [Beyond Incremental Processing: Tracking Concept Drift](https://www.aaai.org/Papers/AAAI/1986/AAAI86-084.pdf) (Jeffrey C. Schlimmer and Richard H. Granger, Jr., 1986) コンセプトドリフト（Concept drift）はまったく新しい概念というわけではありません。
* [Failing Loudly: An Empirical Study of Methods for Detecting Dataset Shift](https://arxiv.org/abs/1810.11953) (Rabanser et al., 2019)
* [Out-of-Distribution Generalization via Risk Extrapolation (REx)](http://proceedings.mlr.press/v139/krueger21a.html) (Krueger et al., 2020) 
* [Domain Adaptation under Target and Conditional Shift](https://proceedings.mlr.press/v28/zhang13d.html) (Zhang et al., 2013)
* [A Review of Domain Adaptation without Target Labels](https://ieeexplore.ieee.org/abstract/document/8861136) (Kouw et al., 2019)
* [On Learning Invariant Representations for Domain Adaptation](http://proceedings.mlr.press/v97/zhao19a.html) (Zhao et al., 2019)
* [How to deal with the seasonality of a market?](https://eng.lyft.com/how-to-deal-with-the-seasonality-of-a-market-584cc94d6b75) (Marguerite Graveleau, Lyft Engineering 2019)
* [Invariant Risk Minimization](https://arxiv.org/abs/1907.02893) (Arjovsky et al., 2019) 
* [Causality for Machine Learning](https://arxiv.org/abs/1911.10500) (Bernhard Schölkopf, 2019)


## 9章.実現場での継続学習とテスト

* [Application deployment and testing strategies](https://cloud.google.com/solutions/application-deployment-and-testing-strategies) (Google)
* [MLOps: Continuous delivery and automation pipelines in machine learning](https://cloud.google.com/architecture/mlops-continuous-delivery-and-automation-pipelines-in-machine-learning) (Google)
* [Automated Canary Analysis at Netflix with Kayenta](https://netflixtechblog.com/automated-canary-analysis-at-netflix-with-kayenta-3260bc7acc69) (Michael Graff and Chris Sanden, Netflix Technology Blog 2018)


### 文脈バンディット

* [A/B testing — Is there a better way? An exploration of multi-armed bandits](https://towardsdatascience.com/a-b-testing-is-there-a-better-way-an-exploration-of-multi-armed-bandits-98ca927b357d) (Greg Rafferty, Towards Data Science 2020)
* [Deep Bayesian Bandits: Exploring in Online Personalized Recommendations](https://arxiv.org/abs/2008.00727) (Guo et al. 2020)
* [Active Learning and Contextual Bandits](http://www.machinedlearnings.com/2012/02/active-learning-and-contextual-bandits.html) (Paul Mineiro, 2012) 


## 10章.MLOpsにおけるインフラとツール

* [Introduction to Microservices, Docker, and Kubernetes](https://www.youtube.com/watch?v=1xo-0gCVhTU): DockerとKubernetes（k8s）の基礎知識に関する1時間の動画。
* [How Microsoft plans efficient workloads with DevOps](https://docs.microsoft.com/en-us/azure/devops/learn/devops-at-microsoft/release-flow)
* [Airbnb’s BigHead](https://vimeo.com/274801958)
* [Uber’s Michelangelo](https://eng.uber.com/michelangelo-machine-learning-platform/)


## 11章.機械学習の人的側面

* [Weapons of Math Destruction](https://www.amazon.com/Weapons-Math-Destruction-Increases-Inequality/dp/0553418815) (Cathy O’Neil, Crown Books 2016)
* [NIST Special Publication 1270](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.1270.pdf): 『Towards a Standard for Identifying and Managing Bias in Artificial Intelligence（人工知能におけるバイアスを識別・対処する標準を目指して）』
* ACM Conference on Fairness, Accountability, and Transparency (ACM FAccT) [論文等](https://facctconference.org/)
* [Trustworthy ML](https://www.trustworthyml.org/resources): 信頼性のある機械学習についてより詳しく学びたい研究者や実践者にお勧めする情報源と基礎研究のリスト
* Sara Hookerの素晴らしいスライド [ML Beyond Accuracy: Fairness, Security, Governance](https://docs.google.com/presentation/d/1cshMKKSX24L0RL7LNzyOkZNQHD7N-Zyff8iffrLIVYM/edit?usp=sharing) (2022)
* Timnit Gebru and Emily Dentonの説明責任・透明性・透明性・倫理に関する[チュートリアル](https://sites.google.com/view/fatecv-tutorial/schedule) (2020)
