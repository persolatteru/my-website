<center>

# TCP/IPについて

</center>

**<p align="right">最終更新日:2025/12/09**
**パーソルエクセルHRパートナーズ**
**報告者:中田　敦也</p>**

---
## 目次
[**1.初めに**](#1初めに)
- [1.1 このマークダウンについて](#11-このマークダウンについて)
- [1.2 参考書籍・参考資料](#12-参考書籍参考資料)

[**2.コンピュータネットワークの基礎知識**](#2コンピューターネットワークの基礎知識)
- [2.1 プロトコルとは・プロトコルの種類](#21-プロトコルとはプロトコルの種類)
- [2.2 プロトコルがなぜ必要なのか](#22-プロトコルがなぜ必要なのか)
- [2.3 OSI参照モデル](#23-osi参照モデル)
- [2.4 OSI参照モデルの各階層の役割](#24-osi参照モデルの各層の役割)
- [2.5 OSI参照モデルの通信処理](#25-osi参照モデルの通信処理)
- [2.6 各層の処理詳細](#26-各層の処理詳細)
- [2.7 データ配送の種類](#27-データ配送の種類)
- [2.8 現在の通信方法](#28-現在の通信方法)
- [2.9 通信相手の数による通信方式の分類](#29-通信相手の数による通信方式の分類)
- [2.10 ネットワークの構成要素](#210-ネットワークの構成要素)


- [2.X この章に関連するその他用語](#2x-この章に関連するその他用語)

[**参考文献**](#参考文献)
[**引用詳細**](#引用詳細)

>閲覧したい内容をクリックするとその内容までほかの内容をスキップできる。

---
## 1.初めに
### 1.1 このマークダウンについて
&emsp;このMarkdown（報告書）は報告者が **TCP/IP** について学習を行うために作成する報告書である。報告者が覚える必要のある用語や技術を取り上げてこのMarkdownに記述する。記述方法はMarkdown形式であり、記述方法・閲覧方法に関しては[記述方法.md](/記述方法.md)に記述している。

### 1.2 参考書籍・参考資料
&emsp;主に参考書籍についてはオーム社出版の **「マスタリングTCP/IP　入門編　第６版」** である。ほか参考にした資料等あればその都度、[参考文献](#参考文献)に記述する。

[↑Back to the Top](#tcpipについて)

---
## 2.コンピューターネットワークの基礎知識
### 2.1 プロトコルとは・プロトコルの種類

&emsp;**プロトコル**とはコンピュータとコンピュータがネットワークを利用して通信するために決められた **「約束ごと」** や **「規格」** のようなもののことである。
プロトコルの種類は以下の表のようなものがある。
<center>

表　プロトコルの種類[^1]

</center>

[^1]: オーム社出版　マスタリングTCP/IP　入門編　第６版 P.14から引用

<table style="max-width: 60%; width: 100%; table-layout: fixed; margin: 0 auto; text-align: center;">
    <thread>
        <tr style="background-color: grey;">
            <th>ネットワークアーキテクチャ</th>
            <th>プロトコル</th>
            <th>主な用途</th>
        </tr>    
    </thread>
    <tbody>
        <tr>
            <td style="word-break: break-all;">
                <strong>TCP/IP</strong>
            </td>
            <td style="word-break: break-all;">IP,ICMP,TCP,UDP,HTTP,TELNET,SNMP,SMTP</td>
            <td style="word-break: break-all;">インターネット,LAN</td>
        </tr>
        <tr>
            <td style="word-break: break-all;">
                <strong>IPX/SPX(NetWare)</strong>
            </td>
            <td style="word-break: break-all;">IPX,SPX,NPC</td>
            <td style="word-break: break-all;">パソコンLAN</td>
        </tr>
        <tr>
            <td style="word-break: break-all;">
                <strong>Apple Talk</strong>
            </td>
            <td style="word-break: break-all;">DDP,RTMP,AEP,ATP,ZIP</td>
            <td style="word-break: break-all;">現Apple社製品のLANで使われていた</td>
        </tr>
        <tr>
            <td style="word-break: break-all;">
                <strong>DECnet</strong>
            </td>
            <td style="word-break: break-all;">DPR,NSP,SCP</td>
            <td style="word-break: break-all;">旧DEC社のミニコンピュータなどで使われていた</td>
        </tr>
        <tr>
            <td style="word-break: break-all;">
                <strong>OSI</strong>
            </td>
            <td style="word-break: break-all;">FTAM,MOTIS,VT,CMIS/CMIP,CLNP,CONP</td>
            <td style="word-break: break-all;">-</td>
        </tr>
        <tr>            
            <td style="word-break: break-all;">
                <strong>XNS</strong>
            </td>
            <td style="word-break: break-all;">IDP,SPP,PEP</td>
            <td style="word-break: break-all;">Xerox社ネットワークで主に使われていた</td>
        </tr>
    </tbody>
</table>



### 2.2 プロトコルがなぜ必要なのか
&emsp;コンピューター同士がお互いに通信を行うためには両者が同じプロトコルを理解し、処理できなければならない。そのためプロトコルはとても重要なものになる。
プロトコルを **言語**,コミュニケーションを **通信**,話の内容を **データ** ととらえるとわかりやすくなる。<u>言語が異なるだけでその言語が理解できなくなるため、話の内容つまりデータが取得できなくなる。</u>そのため、コンピュータ間のプロトコルの一致は通信において必要な条件となる。

### 2.3 OSI参照モデル
&emsp;コンピュータ間で通信を行うためにはプロトコルを一致させるつまり標準化を行う必要がある。そのために考えられたのが **OSI参照モデル** である。**OSI参照モデル**では通信に必要な機能を７つの階層に分け、機能を分割することで複雑になりがちなネットワークプロトコルを単純化するためのモデルである。モデルのイメージは以下の図のようになる。

<center>

![OSI参照モデルイメージ](/画像/OSI参照モデル.png)  
&emsp;  
図　OSI参照モデルのプロトコル階層構造イメージ[^2]

</center>

[^2]: ケムファク　OSI参照モデルの基礎知識　から引用

### 2.4 OSI参照モデルの各層の役割

&emsp;OSI参照モデルの各層の役割は以下の表のようになる。
<center>

表　OSI参照モデルの各層の役割[^3]

</center>

[^3]: オーム社出版　マスタリングTCP/IP　入門編　第６版 P.25から引用

<table style="max-width: 70%; width: 100%; table-layout: fixed; margin: 0 auto; text-align: center;">
    <thread>
        <tr style="background-color: grey;">
            <th style="word-break: break-all;"> </th>
            <th style="word-break: break-all;">層</th>
            <th style="word-break: break-all;">機能</th>
        </tr>    
    </thread>
    <tbody>
        <tr>
            <td style="word-break: break-all;">
                <strong>7</strong>
            </td>
            <td>アプリケーション層</td>
            <td style="word-break: break-all;">
                特定のアプリケーションに特化したプロトコル。
            </td>
        </tr>
        <tr>
            <td style="word-break: break-all;">
                <strong>6</strong>            
            </td>
            <td>プレゼンテーション層</td>
            <td style="word-break: break-all;">
                機器固有のデータフォーマットと、ネットワーク共通のデータフォーマットの交換。
            </td>
        </tr>
        <tr>
            <td style="word-break: break-all;">
                <strong>5</strong>
            </td>
            <td>セッション層</td>
            <td style="word-break: break-all;">
                通信の管理。コネクション（データが流れる論理的な通信路）の確立/切断。トランスポート層以下の層の管理。
            </td>
        </tr>
        <tr>
            <td style="word-break: break-all;">
                <strong>4</strong>                        
            </td>
            <td>トランスポート層</td>
            <td style="word-break: break-all;">
                両端ノード間のデータ転送の管理。データ転送の信頼性を提供する（データを確実に相手に届ける役目）。
            </td>
        </tr>
        <tr>
            <td style="word-break: break-all;">
                <strong>3</strong>
            </td>
            <td>ネットワーク層</td>
            <td style="word-break: break-all;">
                アドレスの管理と経路の選択。
            </td>
        </tr>
        <tr>            
            <td style="word-break: break-all;">
                <strong>2</strong>
            </td>
            <td>データリンク層</td>
            <td style="word-break: break-all;">
                直接接続された機器間でのデータフレームの識別と転送。
            </td>
        </tr>
        <tr>                        
            <td style="word-break: break-all;">
                <strong>1</strong>
            </td>
            <td>物理層</td>
            <td style="word-break: break-all;">
                "0"と"1"を電圧の高低や光の点滅に変換する。コネクタやケーブルの形状の規定。
            </td>
        </tr>
    </tbody>
</table>

&emsp;

### 2.5 OSI参照モデルの通信処理
&emsp;送信側では7層、６層と順番に上の層から下の層へデータが伝えられ、受信側では１層、２層と順番に上の層へデータが伝えられる。それぞれの階層では上位層から渡されたデータに自分の階層のプロトコル処理に必要な情報を **ヘッダ** という形で付与する。受信側では受信したデータを処理して **ヘッダ** とその上位層へのデータに分離する。そして、データを上位層へ渡すことで送信したデータが元のデータに復元される。

<center>

![OSI参照モデルの通信処理](/画像/OSI参照モデル通信処理.png)  
&emsp;  
図　OSI参照モデルの通信処理イメージ[^4]

</center>

[^4]:Qiita TCP/IPによる通信処理の流れ   から引用


### 2.6 各層の処理詳細
- [アプリケーション層](#261-アプリケーション層)
- [プレゼンテーション層](#262-プレゼンテーション層)
- [セッション層](#263-セッション層)
- [トランスポート層](#264-トランスポート層)
- [ネットワーク層](#265-ネットワーク層)
- [データリンク層](#266-データリンク層)
- [物理層](#267-物理層)

#### 2.6.1 アプリケーション層
&emsp;アプリケーション層では **メッセージの本文（送りたいデータ）** という情報と **宛先** の情報を表す **ヘッダ** をつけられたデータが送信先のホストのアプリケーションに届けられる。送信先のアプリケーションでは送信された情報（データ）を分析し、何らかのトラブルでデータを受信できない場合はエラー処理を行う。

#### 2.6.2 プレゼンテーション層
&emsp;送信元と送信先でデータ形式の違いからデータを読み取ることができなくなってしまうことを防ぐために共通の形式に変換を行う。送信元の場合は **「元のデータ形式」→「共通のデータ形式」**、送信先の場合は **「共通のデータ形式」→「元のデータ形式」** のような処理となる。

#### 2.6.3 セッション層
&emsp; セッション層ではデータの送信方法(通信経路や通信方法)の **制御(通信の効率化)** を行っている。

`例）複数のメッセージを順番に送信する。or 複数のメッセージを同時に並列送信する。`

#### 2.6.4 トランスポート層
&emsp;トランスポート層では[コネクションの確立](#2x-この章に関連するその他用語)を行い、通信が終了したらコネクションを切断する。また、送信先にデータがしっかりと送信できなかった場合に **再送** する役割もある。

#### 2.6.5 ネットワーク層
&emsp;下図のようにネットワーク間の通信を行い、データを配達する。ネットワーク間に様々なデータリンクが存在していても送信できるようにしている。このようにしてデータリンク層及び通信全体の **通信の信頼性** を向上させている。

<center>

![各層の通信イメージ](/画像/各層の通信イメージ.png)  
&emsp;  
図　各層の通信イメージ[^5]
[^5]:株式会社　日立情報通信エンジニアリング　OSI参照モデルの話（第２回）から引用

</center>

#### 2.6.6 データリンク層
&emsp;データリンク層では[2.6.5](#265-ネットワーク層)で示した図のように通信媒体で直接接続された機器同士でデータのやり取りをできるようにする役割を持つ。

#### 2.6.7 物理層
&emsp;物理層では、データの０や１を電圧や光のパルスに変換して物理的な通信媒体に流す。MACアドレスの情報を含むヘッダが、ネットワーク層から渡されたデータにつけられて実際のネットワークに流される。

#### 2.7 データ配送の種類
&emsp;データ配送には主に２種類ある。

* **コネクション型**
&emsp;データを送信する前に送信ホストと受信ホストの間で回線の 接続をする。コネクション型の場合には通信の前後にコネクションの確立と切断の処理を行う必要があるが、相手が通信不能の場合は下のイメージ図のようにパケットロスしてしまった分のデータだけを送信すればよいので、相手に無駄なデータを送らずに済む通信方法。

&emsp;

* **コネクションレス型**
&emsp;コネクションの確立や切断処理がなく、送信者がいつでもデータを送信することのできる送信方法。受信相手の確認を行わないため、受信相手がいない場合や相手に届かない場合にもデータを送信することができる。


<center>

![通信方法種類イメージ図](/画像/通信方法種類イメージ.png)  
&emsp;  
図　通信方法のイメージ図[^6]
[^6]:note UDPとTCP、構造・仕組みの違いを解説から引用

</center>

### 2.8 現在の通信方法
&emsp;現在、通信方法として主に２種類が使用されている。
&emsp;

* **回線交換**
&emsp;回線交換の方法では交換機がデータの中継処理を行う。コンピューターは交換機に接続され、交換機間は<u>複数の回線</u>で接続される。通信したい場合、交換機を通して目的のコンピュータとの間に回線を設定する。<u>回線を接続すると切断されるまで</u>その回線を **占有利用** する。
&emsp;
***⇒通信が終了するまでほかのコンピュータ(通信を行っていない第3者)が接続できなくなる。***

<center>

![回線交換イメージ図](/画像/回線交換イメージ.png)  
&emsp;  
図2.8-1　回線交換のイメージ図[^7]
[^7]:ITパスポート試験ドットコム(H28 春 Q71)から引用

</center>

* **パケット交換**
&emsp;回線に接続しているコンピュータが送信するデータを **<u>複数のパケットに分け、転送の順番を待つ行列に並べる</u>** 通信方法。ネットワークの混雑度によってパケットの到着速度が変わり、ルータのバッファがいっぱいになり、あふれるほど大量のパケットが流れると、パケットが喪失して相手に届かなくなる場合もある。
&emsp;
***⇒各コンピュータが一斉に送受信でき、回線を効率的に利用できる。***

<center>

![パケット交換イメージ図](/画像/パケット交換イメージ.png)  
&emsp;  
図2.8-2　パケット交換のイメージ図[^8]
[^8]:ITパスポート試験ドットコム(H28 春 Q71)から引用

</center>

### 2.9 通信相手の数による通信方式の分類
<center>

表　通信方式の分類[^9]
[^9]:オーム社出版　マスタリングTCP/IP　入門編　第６版 P.39-40から引用

</center>

<table style="max-width: 80%; width: 100%; table-layout: fixed; margin: 0 auto; text-align: center;">
    <thread>
        <tr style="background-color: grey;">
            <th style="word-break: break-all;">通信方式</th>
            <th style="word-break: break-all;">説明</th>
        </tr>    
    </thread>
    <tbody>
        <tr>
            <td>
                <strong>ユニキャスト</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">1対1通信。</td>
        </tr>
        <tr>
            <td>
                <strong>ブロードキャスト</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">1台のホストから接続されるすべてのホストへ向けて情報を発信する通信。誰が受信しているのかはわからない。</td>
        </tr>
        <tr>
            <td>
                <strong>マルチキャスト</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">ブロードキャスト同様に複数のホストへ通信を行うが、通信先を特定のグループに限定している通信。</td>
        </tr>
        <tr>
            <td>
                <strong>エニーキャスト</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">特定の複数台へ向けて情報を発信する通信。マルチキャストとは異なり、特定の複数台のうちからネットワーク上で最適な条件を持つ対象が選別され、その対象1つにだけ送信される。以降の通信はそのホストとの間で行われる。</td>
        </tr>
    </tbody>
</table>
&emsp;

### 2.10 ネットワークの構成要素 
&emsp;ネットワークの構成する機器とその役割は以下の図表のようになる。
<center>

表　ネットワークを構成する機器とその役割[^10]
[^10]:オーム社出版　マスタリングTCP/IP　入門編　第６版 P.44から引用

</center>

<table style="max-width: 60%; width: 100%; table-layout: fixed; margin: 0 auto; text-align: center;">
    <thread>
        <tr style="background-color: grey;">
            <th style="word-break: break-all;">機器</th>
            <th style="word-break: break-all;">役割</th>
        </tr>    
    </thread>
    <tbody>
        <tr>
            <td>
                <strong>ネットワークインターフェイス</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">コンピュータをネットワークに接続するための装置</td>
        </tr>
        <tr>
            <td>
                <strong>リピーター</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">ネットワークを物理層で延長する装置</td>
        </tr>
        <tr>
            <td>
                <strong>ブリッジ/レイヤ2スイッチ</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">ネットワークをデータリンク層で延長する装置</td>
        </tr>
        <tr>
            <td>
                <strong>ルーター/レイヤ3スイッチ</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">ネットワーク層によってパケットを転送する装置</td>
        </tr>
        <tr>
            <td>
                <strong>レイヤ4-7 スイッチ</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">
                トランスポート層より上の情報でトラフィックを処理する装置。なお、図には記載されていないが、レイヤ3スイッチとサーバーの間に設置される。            
            </td>
        </tr>
                <tr>
            <td>
                <strong>ゲートウェイ</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">プロトコルの変換をする装置</td>
        </tr>
    </tbody>
</table>

&emsp;

<center>

![ネットワークの構成要素](/画像/ネットワークの構成要素.png)  
&emsp;  
図　ネットワークの構成要素[^11]
[^11]:Hatena Blog 【IT勉強】　2分で読める中小規模のネットワーク構成概要から引用

</center>


### 2.X この章に関連するその他用語

<table style="max-width: 50%; width: 100%; table-layout: fixed; margin: 0 auto; text-align: center;">
    <thread>
        <tr style="background-color: grey;">
            <th style="word-break: break-all;">用語</th>
            <th style="word-break: break-all;">意味</th>
        </tr>    
    </thread>
    <tbody>
        <tr>
            <td>
                <strong>コネクションの確立</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">送信元から送信先への通信経路を確保し、データ送信の準備を行うこと。</td>
        </tr>
        <tr>
            <td>
                <strong>トラフィック</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">ネットワーク回線やサーバーにかかっている通信の負荷や混雑度合いのこと。</td>
        </tr>
        <tr>
            <td>
                <strong></strong>
            </td>
            <td style="word-break: break-all; text-align:left;"></td>
        </tr>
        <tr>
            <td>
                <strong></strong>
            </td>
            <td style="word-break: break-all; text-align:left;"></td>
        </tr>
    </tbody>
</table>
&emsp;

　
[↑Back to the Top](#tcpipについて)

---
## 参考文献
* オーム社出版　マスタリングTCP/IP　入門編　第６版
* ケムファク　OSI参照モデルの基礎知識　
https://chem-fac.com/osi-reference-model/
* Qiita TCP/IPによる通信処理の流れ 
https://qiita.com/be834194/items/d97f5b300dc763b59ec0
* 株式会社　日立情報通信エンジニアリング  OSI参照モデルの話（第２回） 
https://www.hitachi-ite.co.jp/column/20.html
* note UDPとTCP、構造・仕組みの違いを解説 
https://note.com/fscom_japan/n/n95031e679d86
* ITパスポート試験ドットコム  H28 春 問71
https://www.itpassportsiken.com/kakomon/28_haru/q71.html
* Hatena Blog 【IT勉強】　2分で読める中小規模のネットワーク構成概要
https://study-on.hatenablog.com/entry/2020/12/01/200000

[↑Back to the Top](#tcpipについて)

## 引用詳細