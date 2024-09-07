# 子供用 PC 雑記帳

## 子供用アカウントの作成

* Microsoft アカウント
    * Microsoft Family Safety で管理。
    * マイクラと PC ログイン用に使う。
    * メールアドレスが出来る。全て削除するようにルールを作成する。
    * Teams を有効にして情報共有に使う。
    * ゲームの権限設定
        * Xbox [プライバシーとオンラインの安心設定](https://account.xbox.com/ja-jp/settings)で設定する:
    * マイクラで必要な権限
        * Xbox Series X|S、Xbox One、Windows 10 デバイス オンライン セーフティ
            * マルチプレイヤー ゲームへの参加
            * フレンドを追加
        * Xbox 360 オンラインの安心設定
            * オンライン ゲーム
    * AmongUs で必要な権限設定
        *  https://answers.microsoft.com/en-us/xbox/forum/all/among-us-on-pc-not-letting-me-play-online/33e01378-c25a-4d1c-9ff8-fd1d1584e5ae
        * プライバシー
            * コミュニティの作品を確認してアップロードできます > すべての人
            * Xbox Live 以外のユーザーが音声やテキストで通信できるようにする > 許可 (ここむずい)
            * 他のユーザーは音声や文字、招待でコミュニケーションできます > すべての人
        * Xbox Series X|S、Xbox One、Windows 10 デバイス オンライン セーフティ
            * Xbox Live 以外のプレイヤーとプレイできます > 許可
            * クラブの結成と参加ができます > 許可
            * ゲームのプレイ内容を配信 > 許可
            * マルチプレイヤー ゲームへの参加 > 許可
            * フレンドを追加 > 許可
        * Xbox 360 オンラインの安心設定
            * オンライン ゲーム
    * マイクラ Realms や Add On の購入
        * 子供のアカウントで支払いオプション https://account.microsoft.com/billing/payments に行く。
            * クレジットカードを登録
        * 大人のアカウントで Family Safety https://account.microsoft.com/family/home に行く
            * 子供の名前を選択 > 支出 > クレジットカード
                * 購入するたびに承認が必要 を off にする。
            * マイクラ内の子供のアカウントで Realms を購入する。
            * 購入するたびに承認が必要 を on に戻す。
    * Among U
* Google アカウント
    * Youtube に使う。
    * Google Drive で親のディレクトリを一つ共有。ファイル共有に使う。
* Edge ブラウザの設定
    * 子供アカウントでログイン
    * uBlock Origin を利用

## 統合版 add-on の作り方

* 公式サイト: https://www.minecraft.net/ja-jp/creator
* Minecraft: Bedrock Edition Creator Documentation: https://learn.microsoft.com/en-us/minecraft/creator/
* Getting Started: https://learn.microsoft.com/en-us/minecraft/creator/documents/gettingstarted

* データディレクトリの場所:
    * Win+R %localappdata%\Packages\Microsoft.MinecraftUWP_8wekyb3d8bbwe\LocalState\games\com.mojang

* サンプル: https://github.com/microsoft/minecraft-samples/
* デフォルトのhttps://github.com/Mojang/bedrock-samples

## マイクラ Add-on を共有する際の mcaddon ファイルの作り方

探し方が悪いのか公式の mcaddon の作り方が見つからないのでメモ。以下の方法で作成できる。

* Behavior pack と Resource pack それぞれをあるディレクトリに置く。ディレクトリ名は何でもよいが、英文字にする。例: b/ と r/。日本語を使うと Windows で圧縮した際に文字化けして Minecraft が ZIP フォーマットエラーになる。
* Behavior pack と Resource pack を選択して右クリック > ZIP ファイルに圧縮する。
* ファイル名を決定するときに拡張子を .mcaddon にする。

## Blockbench https://www.blockbench.net/

Blockbench で Minecraft Entity を扱うための基礎知識
https://www.blockbench.net/wiki/guides/bedrock-modeling/

ローポリ創作ツールとあるが、Minecraft Entity Plugin を使えば簡単に Minecraft Add-on の作成ができる。
https://learn.microsoft.com/en-us/minecraft/creator/documents/minecraftentitywizard

File > Plugins... > Minecraft Entity Wizard などをインストール

TODO:

* [クラフターズ・コロニー](https://minecraft-mcworld.com/)
* アニメーション (いまここ)
    * Addon のアニメーション仕様の調査
        * [Creating New Entity Types | Microsoft Learn](https://learn.microsoft.com/en-us/minecraft/creator/documents/introductiontoaddentity)
    * Blockbench でのアニメーション作成方法
* Player モデルにマントなどを追加する方法。
    * 単にボックスを追加するだけでは他のパーツと UV が被ってしまう。
    * https://www.blockbench.net/wiki/guides/bedrock-modeling/ に Blockbench で Entity を作る方法が書いてある。
* Blockbench の翻訳
    * github: https://github.com/JannisX11/blockbench
    * 実行方法
        * npm run bundle
        * npm run dev
    * Blockbench 本体の翻訳: https://www.blockbench.net/wiki/blockbench/localization
        * [Blockbench Translation Project](https://poeditor.com/join/project/EFP1ygSsn7)
        * 翻訳ファイル編集方法
            * https://github.com/JannisX11/blockbench/blob/master/lang/ja.json を編集。
* Wizard の翻訳
    * Plugin: https://github.com/JannisX11/blockbench-plugins
    * Wizard のビルド済み javascript コードは見つかったが、元のソースは見つからなかった。
* done: Player モデル使って Entity を作る方法
    * 目標: 形は魔理沙で動きはハチの Entity。
    * bedrock-samples 内のモデルで何か作ってみる。-> ender_dragon などは部品が足りない。
    * File > New > Minecraft Skin で空のスキンを作る。
        * スキン作成時にダウンロードしたスキン png を指定する。
    * Entity Wizard で適当な Entity を作る。Visual Studio Code を開いておく。
    * モデルをいったん全部消す。
    * File > 読み込み > オープンプロジェクトの読み込み。
    * 先ほど作成したスキンのプロジェクトを選択すると、スキンのモデルが読み込まれる。
    * VSCode で textures/entity/ に png がある事を確認。
    * これを novaskin などからダウンロードした好きなスキンに置き換える。
    * 置き換えた後さらに Blockbench で編集できる。
* done: エンティティの再編集
    * development_resource_packs 内の models/entity/*.get.json ファイルを開ける。
    * Blockbench は development_resource_packs 内を直接編集するので、即時反映される。
* Realms で作成した addon を使う方法
    * 開発中の addon は development_behavior_packs に入っているが Realms で利用するためには behavior_packs に入れる必要がある。これには二つの方法がある。
        * 手動で development_behavior_packs を behavior_packs に移動する。resource pack は移動する必要なし。
            * 簡単だが、新しく作ったモデルを既存の behavior_pack に追加できないので難しいかも。
        * mcaddon を作成してマイクラに読む。
            * Tools > Entity Wizard で作り直し、Blockbench 編集中のモデルを選択すれば再度 mcaddon として export できる。
    * todo: MCreator など、別ツールを使えば mcaddon 化できるかもしれないので調査。


## ゆっくり音声

* 音源: https://www.a-quest.com/demo/
* デモ例: https://www.yukumo.net/

## Minecraft Java Mod を使ったマルチプレイの方法

* CurseForge を起動
* Profile 機能でマイクラのバージョンと Mod を合わせて起動。
* 一人目が LAN に公開する。ポート番号を記載する、もしくは 55555 のように指定する。
* 一人目の IP アドレスを確認する。(mDNS の使い方を要調査)
* 一人目の設定画面で ファイアウォールによるアプリケーションの許可 > javaw.exe を public private 両方許可する必要がある。
* 二人目以降はマルチプレイで IP アドレス:ポート番号を指定する。例: 192.168.100.23:50415

Windows で mDNS を使う方法

* デフォルトで有効になっているので、マシン名を変更する。
* Windows にはデフォルトで ping が通らないので有効化する。
    * Windows セキュリティ > 詳細設定 > 受信の規則 > コアネットワーク - ICMPv4, ICMPv6 受信のプライベート,パブリック > 右クリックで規則の有効化
    * これで `ping マシン名.local` で導通確認が可能。

## CurseForge で起動した Minecraft JAVA 版が遅い時

* 参考 https://rabbitprogram.com/archives/1434
* Nvidia Control Panel を開く
* 3D 設定の管理
* プログラム設定
* 追加
* OpenJDK Platform binary を追加する (c:\users\xxx\curseforge\minecraft\install\runtime\java-runtime-gamma 以下にある。)
* 高パフォーマンス NVIDIA プロセッサを選択
* 適用してマイクラ再起動

## Windows で nvim が使えるようになるまで

## Windows その他設定

* CAPS -> CRTL
    * https://learn.microsoft.com/ja-jp/sysinternals/downloads/ctrl2cap
    * 管理者として cmd.exe を起動
    * `ctrl2cap /install`

## Minecraft Java server

https://www.minecraft.net/ja-jp/download/server

起動

    java -Xmx1024M -Xms1024M -jar server.jar --initSettings

エラーが出る。

    sed -i '' 's/eula=false/eula=true/g' eula.txt

再度起動

    java -Xmx1024M -Xms1024M -jar server.jar

やり直す

    rm -r *.json logs versions eula.txt libraries server.properties world

## Roblox Studio

自作ワールドを公開する条件

* ゲームの環境設定 > プライバシー: 公開
* Roblox に公開

## Nintendo Switch

* スプラを二台のスイッチで遊ぶ方法
    * 結果こうなります。
        * 子供1がスイッチ1で遊ぶ。
        * 子供2がスイッチ2で遊ぶ。他の子もスイッチ2で遊べる。
    * 操作方法
    * 子供1の「いつもあそぶ本体」をスイッチ2にする。
        * [スプラトゥーン3ソフト1つで2人で遊ぶやり方は？2台スイッチがあればふたりで遊ぶことが可能！](https://koris1.com/splatoon3-two-player)
        * [【Switch】「いつもあそぶ本体」の登録・確認・変更方法は？](https://support-jp.nintendo.com/app/answers/detail/a_id/36096/)
    * 子供1がスイッチ2でスプラを購入する。
    * すると子供1はスイッチ1でもスプラを遊べる。スイッチ2では誰でもスプラを遊べる。
