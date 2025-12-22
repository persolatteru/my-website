<center>

# TCP/IPについて

</center>

**<p align="right">最終更新日:2025/12/22**
**パーソルエクセルHRパートナーズ**
**報告者:中田　敦也</p>**

---
## 目次
[**1.ネットワークの構成要素**](#1ネットワークの構成要素)
- [1.1 ネットワークの構成要素](#11-ネットワークの構成要素)
- [1.2 各構成要素詳細](#12-各構成要素詳細)
- [1.3 通信媒体とデータリンクについて](#13-通信媒体とデータリンク)

- [1.X この章に関連するその他用語]()

[**2.現在のネットワークの全体像**]()
- [2.1 ]()
- [2.2 ]()
- [2.3 ]()
- [2.4 ]()


- [1.8 ]()
- [1.9 ]()
- [1.10 ]()

- [1.X この章に関連するその他用語]()


[**参考文献**](#参考文献)
[**引用詳細**](#引用詳細)

>閲覧したい内容をクリックするとその内容までほかの内容をスキップできる。

---
## 1.ネットワークの構成要素
### 1.1 ネットワークの構成要素
&emsp;ネットワークの構成要素は以下の図表の通りである。

<center>

![ネットワークの構成要素](/画像/ネットワークの構成要素.png)
1.1-1 ネットワークの構成要素[^1]

</center>

&emsp;1.1-1の図には示されていないが、通常レイヤ4-7スイッチはレイヤ3スイッチとサーバーの間に配置される。

<center>

1.1-2 ネットワークを構成する機器とその役割[^2]

</center>

[^1]:Hatena Blog 【IT勉強】　2分で読める中小規模のネットワーク構成概要から引用
[^2]:オーム社出版　マスタリングTCP/IP　入門編　第６版 P.44から引用

<table style="max-width: 100%; width: 100%; table-layout: fixed; margin: 0 auto; text-align: center;">
    <thread>
        <tr style="background-color: grey;">
            <th>機器</th>
            <th>役割</th>
            <th>解説箇所</th>
        </tr>    
    </thread>
    <tbody>
        <tr>
            <td style="word-break: break-all;">
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
            <td style="word-break: break-all;">
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
            <td style="word-break: break-all;">
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
            <td style="word-break: break-all;">
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
            <td style="word-break: break-all;">
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
1.2.1-1 NIC（ネットワークインターフェイスカード）[^3]

</center>

[^3]:AscentOptics NIC の役割を理解する: 主要なネットワーク インターフェイス ソリューションから引用

#### 1.2.2 リピーター
&emsp;OSI参照モデルの第１層の物理層でネットワークを延長する機器である。通信媒体を変換できるリピーターも存在する。
>例：同軸ケーブルと光ファイバーの間の信号を変換することが可能。

<center>

![リピーターの機能](/画像/リピーターの機能.png)
1.2.2-1 リピーターの役割[^4]

</center>

[^4]:Ethernet LAN - Repeater / HUB / Bridge / Switch / Routerから引用

&emsp;リピーターによるネットワークの延長では、リピーターの接続段数に制限がある場合がある。
>10Mbps &nbsp;&nbsp;→ 最大４つのリピーターを多段接続可能。
>100Mbps&nbsp;→ 最大２つのリピーターを接続可能。

#### 1.2.3 ブリッジ/レイヤ2スイッチ
&emsp;OSI参照モデルの第２層、データリンク層でネットワーク同士を接続する装置です。**データリンクのフレーム**（パケット）を認識してブリッジ内部のメモリにいったん蓄積し、接続された相手側のセグメント（ネットワーク）に新たなフレームとして送出する。（多段接続に関する制約はない。）
&emsp;データリンクのフレームには、フレームが正しく届いたかどうかをチェックするための [FCS](#1x-その他関連する用語) と呼ばれるフィールドがある。ブリッジはこのフィールドをチェックして、<u>壊れたフレームをほかのセグメントへ送信しないようにする働きがある。</u> また、アドレスの学習機能とフィルタリング機能により、<u>無駄なトラフィックを流さないように制御する。</u>多くのブリッジは、隣のセグメントに流すかどうかの判断を行う機能を実施している。一度そのブリッジを通過したフレームのMACアドレスは、一定期間ブリッジ内部のテーブルに登録され、どのセグメントにどのMACアドレスを持つ機器が存在するのかを判断する仕組みになっている。

<center>

![ブリッジの役割](/画像/ブリッジの役割.png)
1.2.3-1 ブリッジの役割[^5]

</center>

[^5]:オーム社出版　マスタリングTCP/IP　入門編　第６版 P.48を基に図を作成

#### 1.2.4 ルーター/レイヤ3スイッチ
&emsp;OSI参照モデルの第３層、ネットワーク層の処理を行う。ネットワークとネットワークを接続して、パケットを中継する役割がある。ルーター/レイヤ３スイッチは、ネットワーク層のアドレス（**IPアドレス**）で処理を行う。ルーターは異なるデータリンクを相互に接続でき、イーサネットとイーサネット、イーサネットと無線LANといった接続を可能とする。また、ルーターはネットワークの負荷を仕切る役割も行う。

<center>

![ルーターの役割](/画像/router.png)
1.2.4-1 ルーターの役割[^6]

</center>

[^6]:オーム社出版　マスタリングTCP/IP　入門編　第６版 P.50を基に図を作成

#### 1.2.5 レイヤ4-7スイッチ
&emsp;

#### 1.2.6 ゲートウェイ
&emsp;

### 1.3 通信媒体とデータリンク
&emsp;

### 1.X その他関連する用語
<table style="max-width: 100%; width: 100%; table-layout: fixed; margin: 0 auto; text-align: center;">
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


[↑Back to the Top](#tcpipについて)

---
## 2.現在のネットワークの全体像


　
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


[↑Back to the Top](#tcpipについて)

## 引用詳細