<center>

# TCP/IPについて

</center>

**<p align="right">最終更新日:2025/12/24**
**パーソルエクセルHRパートナーズ**
**中田　敦也</p>**

---
## 目次
[**0.コンピュータネットワークの基礎知識**](#0コンピューターネットワークの基礎知識)
- [0.1 プロトコルとは・プロトコルの種類](#01-プロトコルとはプロトコルの種類)
- [0.2 プロトコルがなぜ必要なのか](#02-プロトコルがなぜ必要なのか)
- [0.3 OSI参照モデル](#03-osi参照モデル)
- [0.4 OSI参照モデルの各階層の役割](#04-osi参照モデルの各層の役割)
- [0.5 OSI参照モデルの通信処理](#05-osi参照モデルの通信処理)
- [0.6 各層の処理詳細](#06-各層の処理詳細)
- [0.7 データ配送の種類](#07-データ配送の種類)
- [0.8 現在の通信方法](#08-現在の通信方法)
- [0.9 通信相手の数による通信方式の分類](#09-通信相手の数による通信方式の分類)


- [0.X この章に関連するその他用語](#0x-この章に関連するその他用語)

[**1.ネットワークの構成要素**](#1ネットワークの構成要素)
- [1.1 ネットワークの構成要素](#11-ネットワークの構成要素)
- [1.2 各構成要素詳細](#12-各構成要素詳細)
- [1.3 通信媒体とデータリンクについて](#13-通信媒体とデータリンク)

- [1.X この章に関連するその他用語](#1x-その他関連する用語)

[**2.TCP/IPの階層モデル**](#2tcpipの階層モデル)
- [2.1 TCP/IPとOSI参照モデル](#21-tcpipとosi参照モデル)
- [2.2 TCP/IPの各層の詳細](#22-tcpipの各層の詳細)
- [2.3 TCP/IPの階層モデルと通信例](#23-tcpipの階層モデルと通信例)
- [2.4 ]()
- [2.X この章に関連するその他用語]()


[**参考文献**](#参考文献)
[**引用詳細**](#引用詳細)

>閲覧したい内容をクリックするとその内容までほかの内容をスキップできる。

---
## 0.コンピューターネットワークの基礎知識
### 0.1 プロトコルとは・プロトコルの種類

&emsp;**プロトコル**とはコンピュータとコンピュータがネットワークを利用して通信するために決められた **「約束ごと」** や **「規格」** のようなもののことである。
プロトコルの種類は以下の表のようなものがある。
<center>

0.1-1　プロトコルの種類[^1]

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



### 0.2 プロトコルがなぜ必要なのか
&emsp;コンピューター同士がお互いに通信を行うためには両者が同じプロトコルを理解し、処理できなければならない。そのためプロトコルはとても重要なものになる。
プロトコルを **言語**,コミュニケーションを **通信**,話の内容を **データ** ととらえるとわかりやすくなる。<u>言語が異なるだけでその言語が理解できなくなるため、話の内容つまりデータが取得できなくなる。</u>そのため、コンピュータ間のプロトコルの一致は通信において必要な条件となる。

### 0.3 OSI参照モデル
&emsp;コンピュータ間で通信を行うためにはプロトコルを一致させるつまり標準化を行う必要がある。そのために考えられたのが **OSI参照モデル** である。**OSI参照モデル**では通信に必要な機能を７つの階層に分け、機能を分割することで複雑になりがちなネットワークプロトコルを単純化するためのモデルである。モデルのイメージは以下の図のようになる。

<center>

![OSI参照モデルイメージ](/画像/OSI参照モデル.png)  
&emsp;  
0.3-1　OSI参照モデルのプロトコル階層構造イメージ[^2]

</center>

[^2]: ケムファク　OSI参照モデルの基礎知識　から引用

### 0.4 OSI参照モデルの各層の役割

&emsp;OSI参照モデルの各層の役割は以下の表のようになる。
<center>

0.4-1　OSI参照モデルの各層の役割[^3]

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

### 0.5 OSI参照モデルの通信処理
&emsp;送信側では7層、６層と順番に上の層から下の層へデータが伝えられ、受信側では１層、２層と順番に上の層へデータが伝えられる。それぞれの階層では上位層から渡されたデータに自分の階層のプロトコル処理に必要な情報を **ヘッダ** という形で付与する。受信側では受信したデータを処理して **ヘッダ** とその上位層へのデータに分離する。そして、データを上位層へ渡すことで送信したデータが元のデータに復元される。

<center>

![OSI参照モデルの通信処理](/画像/OSI参照モデル通信処理.png)  
&emsp;  
0.5-1　OSI参照モデルの通信処理イメージ[^4]

</center>

[^4]:Qiita TCP/IPによる通信処理の流れ   から引用


### 0.6 各層の処理詳細
- [アプリケーション層](#061-アプリケーション層)
- [プレゼンテーション層](#062-プレゼンテーション層)
- [セッション層](#063-セッション層)
- [トランスポート層](#064-トランスポート層)
- [ネットワーク層](#065-ネットワーク層)
- [データリンク層](#066-データリンク層)
- [物理層](#067-物理層)

#### 0.6.1 アプリケーション層
&emsp;アプリケーション層では **メッセージの本文（送りたいデータ）** という情報と **宛先** の情報を表す **ヘッダ** をつけられたデータが送信先のホストのアプリケーションに届けられる。送信先のアプリケーションでは送信された情報（データ）を分析し、何らかのトラブルでデータを受信できない場合はエラー処理を行う。

#### 0.6.2 プレゼンテーション層
&emsp;送信元と送信先でデータ形式の違いからデータを読み取ることができなくなってしまうことを防ぐために共通の形式に変換を行う。送信元の場合は **「元のデータ形式」→「共通のデータ形式」**、送信先の場合は **「共通のデータ形式」→「元のデータ形式」** のような処理となる。

#### 0.6.3 セッション層
&emsp; セッション層ではデータの送信方法(通信経路や通信方法)の **制御(通信の効率化)** を行っている。

`例）複数のメッセージを順番に送信する。or 複数のメッセージを同時に並列送信する。`

#### 0.6.4 トランスポート層
&emsp;トランスポート層では[コネクションの確立](#0x-この章に関連するその他用語)を行い、通信が終了したらコネクションを切断する。また、送信先にデータがしっかりと送信できなかった場合に **再送** する役割もある。

#### 0.6.5 ネットワーク層
&emsp;下図のようにネットワーク間の通信を行い、データを配達する。ネットワーク間に様々なデータリンクが存在していても送信できるようにしている。このようにしてデータリンク層及び通信全体の **通信の信頼性** を向上させている。

<center>

![各層の通信イメージ](/画像/各層の通信イメージ.png)  
&emsp;  
0.6.5-1　各層の通信イメージ[^5]
[^5]:株式会社　日立情報通信エンジニアリング　OSI参照モデルの話（第２回）から引用

</center>

#### 0.6.6 データリンク層
&emsp;データリンク層では[0.6.5](#065-ネットワーク層)で示した図のように通信媒体で直接接続された機器同士でデータのやり取りをできるようにする役割を持つ。

#### 0.6.7 物理層
&emsp;物理層では、データの０や１を電圧や光のパルスに変換して物理的な通信媒体に流す。MACアドレスの情報を含むヘッダが、ネットワーク層から渡されたデータにつけられて実際のネットワークに流される。

#### 0.7 データ配送の種類
&emsp;データ配送には主に２種類ある。

* **コネクション型**
&emsp;データを送信する前に送信ホストと受信ホストの間で回線の 接続をする。コネクション型の場合には通信の前後にコネクションの確立と切断の処理を行う必要があるが、相手が通信不能の場合は下のイメージ図のようにパケットロスしてしまった分のデータだけを送信すればよいので、相手に無駄なデータを送らずに済む通信方法。

&emsp;

* **コネクションレス型**
&emsp;コネクションの確立や切断処理がなく、送信者がいつでもデータを送信することのできる送信方法。受信相手の確認を行わないため、受信相手がいない場合や相手に届かない場合にもデータを送信することができる。


<center>

![通信方法種類イメージ図](/画像/通信方法種類イメージ.png)  
&emsp;  
0.7-1　通信方法のイメージ図[^6]
[^6]:note UDPとTCP、構造・仕組みの違いを解説から引用

</center>

### 0.8 現在の通信方法
&emsp;現在、通信方法として主に２種類が使用されている。
&emsp;

* **回線交換**
&emsp;回線交換の方法では交換機がデータの中継処理を行う。コンピューターは交換機に接続され、交換機間は<u>複数の回線</u>で接続される。通信したい場合、交換機を通して目的のコンピュータとの間に回線を設定する。<u>回線を接続すると切断されるまで</u>その回線を **占有利用** する。
&emsp;
***⇒通信が終了するまでほかのコンピュータ(通信を行っていない第3者)が接続できなくなる。***

<center>

![回線交換イメージ図](/画像/回線交換イメージ.png)  
&emsp;  
0.8-1　回線交換のイメージ図[^7]
[^7]:ITパスポート試験ドットコム(H28 春 Q71)から引用

</center>

* **パケット交換**
&emsp;回線に接続しているコンピュータが送信するデータを **<u>複数のパケットに分け、転送の順番を待つ行列に並べる</u>** 通信方法。ネットワークの混雑度によってパケットの到着速度が変わり、ルータのバッファがいっぱいになり、あふれるほど大量のパケットが流れると、パケットが喪失して相手に届かなくなる場合もある。
&emsp;
***⇒各コンピュータが一斉に送受信でき、回線を効率的に利用できる。***

<center>

![パケット交換イメージ図](/画像/パケット交換イメージ.png)  
&emsp;  
0.8-2　パケット交換のイメージ図[^8]
[^8]:ITパスポート試験ドットコム(H28 春 Q71)から引用

</center>

### 0.9 通信相手の数による通信方式の分類
<center>

0.9-1　通信方式の分類[^9]
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


### 0.X この章に関連するその他用語

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
    </tbody>
</table>
&emsp;

[↑Back to the Top](#tcpipについて)

---
## 1.ネットワークの構成要素
### 1.1 ネットワークの構成要素
&emsp;ネットワークの構成要素は以下の図表の通りである。

<center>

![ネットワークの構成要素](/画像/ネットワークの構成要素.png)
1.1-1 ネットワークの構成要素[^10]

</center>

&emsp;1.1-1の図には示されていないが、通常レイヤ4-7スイッチはレイヤ3スイッチとサーバーの間に配置される。

<center>

1.1-2 ネットワークを構成する機器とその役割[^11]

</center>

[^10]:Hatena Blog 【IT勉強】　2分で読める中小規模のネットワーク構成概要から引用
[^11]:オーム社出版　マスタリングTCP/IP　入門編　第６版 P.44から引用

<table style="max-width: 100%; width: 80%; table-layout: fixed; margin: 0 auto; text-align: center;">
    <thread>
        <tr style="background-color: grey;">
            <th>機器</th>
            <th>役割</th>
            <th>解説箇所</th>
        </tr>    
    </thread>
    <tbody>
        <tr>
            <td>
                <strong>ネットワークインターフェイス</strong>
            </td>
            <td style="word-break: break-all;">
                コンピューターをネットワークに接続するための装置
            </td>
            <td style="word-break: break-all;">
                <a href="#121-ネットワークインターフェイス">1.2.1</a>
            </td>
        </tr>
        <tr>
            <td>
                <strong>リピーター</strong>
            </td>
            <td style="word-break: break-all;">
                    ネットワークを物理層で延長する装置
            </td>
            <td style="word-break: break-all;">
                <a href="#122-リピーター">1.2.2</a>
            </td>
        </tr>
        <tr>
            <td>
                <strong>ブリッジ/レイヤ2スイッチ</strong>
            </td>
            <td style="word-break: break-all;">
                ネットワークをデータリンク層で延長する装置
            </td>
            <td style="word-break: break-all;">
                <a href="#123-ブリッジレイヤ2スイッチ">1.2.3</a>
            </td>
        </tr>
        <tr>
            <td style="word-break: break-all;">
                <strong>ルーター/レイヤ3スイッチ</strong>
            </td>
            <td style="word-break: break-all;">
                ネットワーク層によってパケットを転送する装置
            </td>
            <td style="word-break: break-all;">
                <a href="#124-ルーターレイヤ3スイッチ">1.2.4</a>
            </td>
        </tr>
        <tr>
            <td>
                <strong>レイヤ4-7スイッチ</strong>
            </td>
            <td style="word-break: break-all;">
                トランスポート層より上の情報でトラフィックを処理する装置
            </td>
            <td style="word-break: break-all;">
                <a href="#125-レイヤ4-7スイッチ">1.2.5</a>
            </td>
        </tr>
        <tr>
            <td>
                <strong>ゲートウェイ</strong>
            </td>
            <td style="word-break: break-all;">
                プロトコルの変換をする装置
            </td>
            <td style="word-break: break-all;">
                <a href="#126-ゲートウェイ">1.2.6</a>
            </td>
        </tr>
    </tbody>
</table>

### 1.2 各構成要素詳細
>各構成要素の記載場所は[1.1-2](#11-ネットワークの構成要素)に記載している。

#### 1.2.1 ネットワークインターフェイス
&emsp;ネットワークに接続するには専用のインターフェースが必要になる。そのインターフェイスを **ネットワークインターフェイス** と呼ぶ。

<center>

![NIC](/画像/NIC.png)
1.2.1-1 NIC（ネットワークインターフェイスカード）[^12]

</center>

[^12]:AscentOptics NIC の役割を理解する: 主要なネットワーク インターフェイス ソリューションから引用

#### 1.2.2 リピーター
&emsp;OSI参照モデルの第１層の物理層でネットワークを延長する機器である。通信媒体を変換できるリピーターも存在する。
>例：同軸ケーブルと光ファイバーの間の信号を変換することが可能。

<center>

![リピーターの機能](/画像/リピーターの機能.png)
1.2.2-1 リピーターの役割[^13]

</center>

[^13]:Ethernet LAN - Repeater / HUB / Bridge / Switch / Routerから引用

&emsp;リピーターによるネットワークの延長では、リピーターの接続段数に制限がある場合がある。
>10Mbps &nbsp;&nbsp;→ 最大４つのリピーターを多段接続可能。
>100Mbps&nbsp;→ 最大２つのリピーターを接続可能。

#### 1.2.3 ブリッジ/レイヤ2スイッチ
&emsp;OSI参照モデルの第２層、データリンク層でネットワーク同士を接続する装置です。**データリンクのフレーム**（パケット）を認識してブリッジ内部のメモリにいったん蓄積し、接続された相手側のセグメント（ネットワーク）に新たなフレームとして送出する。（多段接続に関する制約はない。）
&emsp;データリンクのフレームには、フレームが正しく届いたかどうかをチェックするための [FCS](#1x-その他関連する用語) と呼ばれるフィールドがある。ブリッジはこのフィールドをチェックして、<u>壊れたフレームをほかのセグメントへ送信しないようにする働きがある。</u> また、アドレスの学習機能とフィルタリング機能により、<u>無駄なトラフィックを流さないように制御する。</u>多くのブリッジは、隣のセグメントに流すかどうかの判断を行う機能を実施している。一度そのブリッジを通過したフレームのMACアドレスは、一定期間ブリッジ内部のテーブルに登録され、どのセグメントにどのMACアドレスを持つ機器が存在するのかを判断する仕組みになっている。

<center>

![ブリッジの役割](/画像/ブリッジの役割.png)
1.2.3-1 ブリッジの役割[^14]

</center>

[^14]:オーム社出版　マスタリングTCP/IP　入門編　第６版 P.48を基に図を作成

#### 1.2.4 ルーター/レイヤ3スイッチ
&emsp;OSI参照モデルの第３層、ネットワーク層の処理を行う。ネットワークとネットワークを接続して、パケットを中継する役割がある。ルーター/レイヤ３スイッチは、ネットワーク層のアドレス（**IPアドレス**）で処理を行う。ルーターは異なるデータリンクを相互に接続でき、イーサネットとイーサネット、イーサネットと無線LANといった接続を可能とする。また、ルーターはネットワークの負荷を仕切る役割も行う。

<center>

![ルーターの役割](/画像/router.png)
1.2.4-1 ルーターの役割[^15]

</center>

[^15]:オーム社出版　マスタリングTCP/IP　入門編　第６版 P.50を基に図を作成

#### 1.2.5 レイヤ4-7スイッチ
&emsp;OSI参照モデルのトランスポート層から<u>アプリケーション層の情報に基づいて配送処理を行う。</u>TCPなどのトランスポート層と、その上のアプリケーション層において、送受信されている通信の内容を分析し、特定の処理を行う。
&emsp;負荷分散のためにサーバーを複数台設置している状況の中で<u>１つのURLを用いて、負荷を分散させる働き</u>を持つ。例えば、ロードバランサーに仮想URLを設定し、利用者へWebサイトとして公開する。この仮想URLを利用者が閲覧すると、ロードバランサーは、<u>複数存在する実際のサーバーへと振り分け</u>、利用者と実際に情報を提供しているサーバーが継続的に利用できるようにセッションを管理する。

<center>

![レイヤ4-7スイッチの役割](/画像/レイヤ4-7スイッチ.png)
1.2.5-1 レイヤ4-7スイッチの役割[^16]

</center>

[^16]:オーム社出版　マスタリングTCP/IP　入門編　第６版 P.51を基に図を作成

#### 1.2.6 ゲートウェイ
&emsp;OSI参照モデルのトランスポート層からアプリケーション層までの階層で、データを変換して中継する装置のことです。特に、お互いに直接通信できない<u>２つの異なる **プロトコル** の翻訳作業を行い、互いに通信できるようにする役割</u>がある。
また、 **アプリケーションゲートウェイ** と呼ばれるwebサービスを利用するときにネットワークトラフィックの軽減やセキュリティを意図して代理サーバー(Proxy Server)を設定する場合がある。

<center>

![ゲートウェイの役割](/画像/ゲートウェイの役割.png)
1.2.5-1 レイヤ4-7スイッチの役割[^17]

</center>

[^17]:オーム社出版　マスタリングTCP/IP　入門編　第６版 P.52を基に図を作成

### 1.3 通信媒体とデータリンク
&emsp;コンピュータネットワークの接続方法としてツイストペアケーブル、光ファイバーケーブル、同軸ケーブル、シリアルケーブルなどが利用される。利用するデータリンクの種類によって、利用するケーブル類が異なる。


<center>

1.3-1 様々なデータリンク[^18]

</center>

[^18]:オーム社出版　マスタリングTCP/IP　入門編　第６版 P.45から引用

<table style="max-width: 100%; width: 80%; table-layout: fixed; margin: 0 auto; text-align: center;">
    <thread>
        <tr style="background-color: grey;">
            <th>データリンク名</th>
            <th>通信媒体</th>
            <th>伝送速度</th>
            <th>主な用途</th>
        </tr>    
    </thread>
    <tbody>
        <tr>
            <td>
                <strong>イーサネット</strong>
            </td>
            <td style="text-align:left;">
                同軸ケーブル
                <br>ツイストペアケーブル</br>
                光ファイバーケーブル
            </td>
            <td>
                10Mbps
                <br>10Mbps~10Gbps</br>
                10Mbps~400Gbps
            </td>
            <td>
                LAN
            </td>
        </tr>
        <tr>
            <td>
                <strong>無線</strong>
            </td>
            <td style="text-align:left;">
                電磁波
            </td>
            <td>
                数Mbps
            </td>
            <td>
                LAN～WAN
            </td>
        </tr>
        <tr>
            <td>
                <strong>ATM</strong>
            </td>
            <td style="text-align:left;">
                ツイストペアケーブル
                <br>光ファイバーケーブル</br>
            </td>
            <td>
                25Mbps,155Mbps
                <br>622Mbps</br>
            </td>
            <td>
                LAN～WAN
            </td>
        </tr>
        <tr>
            <td>
                <strong>FDDI</strong>
            </td>
            <td style="text-align:left;">
                ツイストペアケーブル
                <br>光ファイバーケーブル</br>
            </td>
            <td>
                100Mbps
            </td>
            <td>
                LAN～WAN
            </td>
        </tr>
        <tr>
            <td>
                <strong>フレームリレー</strong>
            </td>
            <td style="text-align:left;">
                ツイストペアケーブル
                <br>光ファイバーケーブル</br>
            </td>
            <td>
                64Kbps～1.5Mbps程度
            </td>
            <td>
                WAN
            </td>
        </tr>
        <tr>
            <td>
                <strong>ISDN</strong>
            </td>
            <td style="text-align:left;">
                ツイストペアケーブル
                <br>光ファイバーケーブル</br>
            </td>
            <td>
                64Kbps～1.5Mbps
            </td>
            <td>
                WAN
            </td>
        </tr>
    </tbody>
</table>



### 1.X その他関連する用語
<table style="max-width: 100%; width: 80%; table-layout: fixed; margin: 0 auto; text-align: center;">
    <thread>
        <tr style="background-color: grey;">
            <th style="word-break: break-all;">用語</th>
            <th style="word-break: break-all;">説明</th>
        </tr>    
    </thread>
    <tbody>
        <tr>
            <td>
                <strong>FCS(Flame Check Sequence)</strong>
            </td>
            <td style="word-break: break-all; text-align:left;">
                ノイズなどにより通信途中でフレームが壊れていないかをチェックする。
            </td>
        </tr>
    </tbody>
</table>
&emsp;


[↑Back to the Top](#tcpipについて)

---
## 2.TCP/IPの階層モデル
### 2.1 TCP/IPとOSI参照モデル
&emsp;OSI参照モデルは「通信プロトコルに必要な機能は何か」を中心に考えてモデル化されているのに対し、TCP/IPの階層モデルは<u>「プロトコルをコンピュータに実装するにはどのようにプログラムしたらよいか」</u>を中心に考えてモデル化されている。

<center>

![TCP/IPの階層モデル](/画像/TCPIP階層モデル.jpg)
2.1-1 TCP/IPの階層モデル[^19]

</center>

[^19]:ビジネス＋IT OSI参照モデルとTCP/IPの階層の違いとは？ から引用

### 2.2 TCP/IPの各層の詳細
- [2.2.1 ハードウェア（物理層）](#221-ハードウェア物理層)
- [2.2.2 ネットワークインターフェース層](#222-ネットワークインターフェース層)
- [2.2.3 インターネット層](#223-インターネット層)
- [2.2.4 トランスポート層](#224-トランスポート層)
- [2.2.2 アプリケーション層](#225-アプリケーション層)

#### 2.2.1 ハードウェア（物理層）
&emsp;TCP/IPの階層モデルでは、最下位層に物理的にデータを転送してくれるハードウェアを置いている。TCP/IPは、ネットワークで接続された装置間で通信できることを前提にして作られているプロトコルであるため、使用する通信媒体はケーブルでも無線でもよく、また、通信するうえでの信頼性やセキュリティ、帯域、遅延時間などについても特に制限なく利用できるようになっている。

#### 2.2.2 ネットワークインターフェース層
&emsp;ネットワークインターフェース層の役割は、NICを動かすための **「デバイスドライバ」** である。利用するコンピュータのOSにデバイスドライバをインストールして、はじめてネットワークインターフェースを利用できる環境が整う。

#### 2.2.3 インターネット層
&emsp;インターネット層ではIPが使用される。**IP** はIPアドレスを基にしてパケットを転送する。

- **IP:** ネットワークをまたいでパケットを配送し、インターネット全体にパケットを送り届けるためのプロトコルである。データリンクの特性を隠す役割もあり、通信したい<u>ホスト間の経路がどのようなデータリンクになっていても通信が可能になる。</u>パケットが相手に届かなくても再送などはしないため、<u>信頼性はない。</u>

- **IMCP:** IPパケットの配送中に **何らかの異常** が発生してパケットを送信できなくなった場合に、<u>パケット元に異常を知らせるために使われるプロトコル。</u>

- **ARP:** パケットの送り先の物理的なアドレス（MACアドレス）をIPアドレスから取得するプロトコル。

<center>

![IPの役割](/画像/IP.jpg)
2.2.3-1 IPの役割[^20]

</center>

[^20]:オーム社出版　マスタリングTCP/IP　入門編　第６版 P.76を基に図を作成 

#### 2.2.4 トランスポート層
&emsp;アプリケーションプログラム間の通信を実現する。どのプログラムとどのプログラムが通信しているのかを **ポート番号** を用いて識別する。
- **TCP:** [コネクション型](#07-データ配送の種類)で<u>信頼性のある</u>トランスポート層のプロトコルである。しかし、コネクションの確立・切断だけで制御のためのパケットを約7回もやり取りするため、<u>転送するデータ総量が少ないときは無駄が多くなってしまう。</u>また、ネットワークの利用効率向上させるための複雑な仕組みがいろいろと組み込まれているため、ビデオ会議の音声・映像データなどの様に<u>一定間隔で決められた量のデータを転送する通信にはあまり向いていない。</u>

- **UDP:** [コネクションレス型](#07-データ配送の種類)で<u>信頼性のない</u>トランスポート層プロトコルである。パケット数の少ない通信や、ブロードキャストやマルチキャストの通信、ビデオや音声などの<u>マルチメディア通信に向いている。</u>

#### 2.2.5 アプリケーション層

&emsp;TCP/IPのアプリケーションの多くは、クライアント/サーバーモデルで作られている。サービスを提供するサーバープログラムは<u>あらかじめホスト上で動作させておかなければならない</u>が、クライアントは<u>いつでも好きな時にサービスを要求することができる。</u>
&emsp;HTTP,SMTP,FTP,TELNETプロトコル,SSHプロトコル,SNMPなどがある。


### 2.3 TCP/IPの階層モデルと通信例
&emsp;


　
[↑Back to the Top](#tcpipについて)

---
## 参考文献
* オーム社出版　マスタリングTCP/IP　入門編　第６版
* Hatena Blog 【IT勉強】　2分で読める中小規模のネットワーク構成概要
https://study-on.hatenablog.com/entry/2020/12/01/200000
* AscentOptics NIC の役割を理解する: 主要なネットワーク インターフェイス ソリューション
https://ascentoptics.com/blog/ja/nic-network/
* Ethernet LAN - Repeater / HUB / Bridge / Switch / Router
https://www.infraexpert.com/study/ethernet6.html
* ビジネス＋IT OSI参照モデルとTCP/IPの階層の違いとは？
https://www.sbbit.jp/article/cont1/12099
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



[↑Back to the Top](#tcpipについて)

## 引用詳細