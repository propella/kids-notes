# 子供用 PC 雑記帳

## 子供用アカウントの作成

* Microsoft アカウント
    * Microsoft Family Safety で管理。
    * マイクラと PC ログイン用に使う。
    * メールアドレスが出来る。全て削除するようにルールを作成する。
    * Teams を有効にして情報共有に使う。
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

## com.mojang の構造

development_ で始まるディレクトリは内容が即更新されて開発に便利な一方で、world にコピーされないので Realms では使えない。
development_ で始まらないディレクトリは作成時に minecraftWorld の各 world ディレクトリにコピーされるため、Realms でも使える。

* behavior_packs: インストールされた behavior pack。インストール時のみ更新。
* resource_packs: インストールされた resource pack。インストール時のみ更新。
* development_behavior_packs: 開発中の behavior pack。ローカルや Realms の world にはコピーされない。内容即時更新。
* development_resource_packs: 開発中の resource pack。ローカルや Realms の world にはコピーされない。内容即時更新。
* minecraftWorlds
    * (ワールドごとの ID)
        * behavior_packs: 有効にした behavior pack がコピーされる。(development_behavior_packs にあるものはコピーされない)
        * resource_packs: 有効にした resource pack がコピーされる。(development_resource_packs にあるものはコピーされない)

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

TODO:

* [クラフターズ・コロニー](https://minecraft-mcworld.com/)
* アニメーション
* Player モデルにマントなどを追加する方法。
    * 単にボックスを追加するだけでは他のパーツと UV が被ってしまう。
    * https://www.blockbench.net/wiki/guides/bedrock-modeling/ に Blockbench で Entity を作る方法が書いてある。
* Blockbench の翻訳
    * github: https://github.com/JannisX11/blockbench
    * 実行方法
        * npm run webpack
        * npm run dev
    * 翻訳ファイル編集方法
        * https://github.com/JannisX11/blockbench/blob/master/lang/ja.json を編集。
* Wizard の翻訳
    * https://www.blockbench.net/wiki/blockbench/localization
    * [Blockbench Translation Project](https://poeditor.com/join/project/EFP1ygSsn7)
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


## 統合版 Add-on に利用できるツール

* MCreator: https://mcreator.net/
    * MCreator は Java 版の Mod 作成を GUI で行うツール。最近統合版 Add-on にも対応したらしい。
* Novaskin: https://minecraft.novaskin.me/
    * Web でスキンの作成ができる。
* Blockbench: https://www.blockbench.net/
    * Web 版もある: https://web.blockbench.net/

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
