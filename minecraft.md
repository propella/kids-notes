# マインクラフトの勉強

---

# [minecraft]マインクラフト2: Creator Learning Journey を眺める。

公式ドキュメントの [Creator Learning Journey](https://learn.microsoft.com/en-us/minecraft/creator/documents/learningjourneyguide?view=minecraft-bedrock-stable) を読むと、マイクラ開発初心者が学ぶべき項目が整理されています。これを読みながらアドオン勉強の道筋を考えます。

## Step1 何がどこにあるか確認しよう

[Getting Started With Minecraft Add-Ons | Microsoft Learn](https://learn.microsoft.com/en-us/minecraft/creator/documents/gettingstarted?view=minecraft-bedrock-stable&tabs=Windows10)

基本的なアドオンの知識について書かれてあります。特に大切なのはアドオンにとっての魔法のパス

    %localappdata%\Packages\Microsoft.MinecraftUWP_8wekyb3d8bbwe\LocalState\games\com.mojang

です。これを Win+R に打ち込むとマイクラのデータディレクトリが開きます。アドオン開発はこの `com.mojang` ディレクトリ内で行います。スタートにピン止め推奨です。

### ビヘイビアパックとリソースパック

アドオンはビヘイビアパックとリソースパックの二種類あります。それぞれ役割が違っていて、あるアドオンをインストールするときは典型的にはビヘイビアパックとリソースパックの両方を読みます。

* リソースパック: 見た目を制御する部品です。クライアント側で動作します。
* ビヘイビアパック: 動きを制御する部品です。サーバ側で動作します。

![Resource pack & Behavior pack](https://learn.microsoft.com/en-us/minecraft/creator/documents/media/addentity/filestructure.png)

参考: [Creating New Entity Types > File structure](https://learn.microsoft.com/en-us/minecraft/creator/documents/introductiontoaddentity?view=minecraft-bedrock-stable#file-structure)

## `com.mojang` の構造

`com.mojang` には以下のようなディレクトリがあります。

* behavior_packs: インストールされたビヘイビアパック。インストール時のみ更新されます。
* resource_packs: インストールされたリソースパック。インストール時のみ更新されます。
* development_behavior_packs: 開発中のビヘイビアパック。ローカルや Realms の world にはコピーされない。内容即時更新。
* development_resource_packs: 開発中のリソースパック。ローカルや Realms の world にはコピーされない。内容即時更新。
* minecraftWorlds
    * (ワールドごとの ID)
        * behavior_packs: 有効にしたビヘイビアパックがコピーされる。(development_behavior_packs にあるものはコピーされない)
        * resource_packs: 有効にしたリソースパックがコピーされる。(development_resource_packs にあるものはコピーされない)

ここで、development_ で始まるディレクトリが開発ように特別に用意されたアドオン用のディレクトリです。以下の違いがあります。

* development_ で始まるディレクトリは内容が即更新されて開発に便利な一方で、world にコピーされないので Realms では使えない。
* development_ で始まらないディレクトリは作成時に minecraftWorld の各 world ディレクトリにコピーされるため、Realms でも使える。

前回 Blockbench で作成したアドオンが Realms で使えないと言った理由はここにあります。Blockbench ではアドオンを development_ で始まるディレクトリに作成するので、マイクラ内の設定で有効にしても minecraftWorlds にコピーされず、Realms サーバにもアップロードされません。

作成したアドオンを Realms で使うには zip で固めて .mcaddon ファイルを作成し、適切にマイクラにインストールさせる必要があります。

[Comprehensive List of Pack Contents](https://learn.microsoft.com/en-us/minecraft/creator/documents/comprehensivepackcontents)

## Step2 何か作ってみよう

この章では、リソースパックとビヘイビアパックの基礎知識を解説しています。

[An Introduction to Resource Packs](https://learn.microsoft.com/en-us/minecraft/creator/documents/resourcepack?view=minecraft-bedrock-stable)

[An Introduction To Behavior Packs](https://learn.microsoft.com/en-us/minecraft/creator/documents/behaviorpack?view=minecraft-bedrock-stable)

ここでのポイントは以下と思いました。

* リソースパックは既存のマイクラの見た目を変更できる。
* 既存の見た目を変更するには、[Vanilla resource pack](https://aka.ms/resourcepacktemplate) でファイル名を調べると良い。
* ビヘイビアパックは既存のマイクラの動きを変更できる。新規のエンティティも作成できる。
    * ビヘイビアパックからリソースパックへの依存を設定すると、依存するリソースパックを自動インストールできる。

## Step3 もっと複雑なものを作ってみよう

読んでないのでリンクだけコピペ

* [Add a Custom Sounds](https://learn.microsoft.com/en-us/minecraft/creator/documents/addcustomsounds)
* [Create an Entity](https://learn.microsoft.com/en-us/minecraft/creator/documents/introductiontoaddentity)
* [Create a Custom Block](https://learn.microsoft.com/en-us/minecraft/creator/documents/addcustomdieblock)
* [Create a Sushi Block: Advanced Custom Blocks](https://learn.microsoft.com/en-us/minecraft/creator/documents/advancedcustomblocks)
* [Create a Custom Item](https://learn.microsoft.com/en-us/minecraft/creator/documents/addcustomitems)

## さらに上級編

* [Commonly Used Tools](https://learn.microsoft.com/en-us/minecraft/creator/documents/commonlyusedtools?view=minecraft-bedrock-stable)
* [Animate a Block Texture](https://learn.microsoft.com/en-us/minecraft/creator/documents/createanimatedblocktexture?view=minecraft-bedrock-stable)
* [Create a Goblin Chef Entity](https://learn.microsoft.com/en-us/minecraft/creator/documents/makerseriesmakingthegoblinchef?view=minecraft-bedrock-stable)
* [Create a Loot Table](https://learn.microsoft.com/en-us/minecraft/creator/documents/createloottable?view=minecraft-bedrock-stable)
* [Create a Village with Structure Blocks](https://learn.microsoft.com/en-us/minecraft/creator/documents/structureblockstutorial?view=minecraft-bedrock-stable)
* [Non-Player Character (NPC) Dialogue](https://learn.microsoft.com/en-us/minecraft/creator/documents/npcdialogue?view=minecraft-bedrock-stable)

とまあこの線に沿って勉強していきます。ただ、飽きてきたので [MCreator](https://mcreator.net/) を調べよっかな。

---

# [minecraft]マインクラフト1: アドオン勉強の記録を始めます。

マインクラフトの素晴らしいところは、一通り普通に遊んだ後で、マーケットプレイスや HIVE など色々な追加機能で無限に遊び方が広がる事です。そのマインクラフトの拡張に中心的な役割を果たすのが「アドオン」という機能です。アドオンというのは zip で固められた設定ファイルのようなもので、既存のスキンや動作を上書きしたり、新しいモブやアイテムを作成できます。アドオンの機能は強力で、マイクラの上に FPS や人狼など、まったく新しいゲームを構築する事すらできてしまいます。

うちの子供たちも、マイクラを初めるとすぐに「アドオンを作りたい！」と言い始めました。その希望を叶えるために半年前から時間を見つけてはアドオンについて調べているのですが、週末の限られた時間しか無く、すぐに調べたことを忘れてしまうので、ここに記録を残しながら調べていく事にします。

## 目標

* 小学生が簡単にマイクラのアドオンを作れる。
* 好きなスキンのドラゴンを作れる。
* かっこいい剣を振るとすごいパーティクルが出る。

## マイクラアドオン基本情報

マイクラアドオン開発に必要な基本的な情報を書きます。まずマイクラには統合版と Java 版という二つの種類があります。ここでは統合版のみ触れます。統合版には任天堂スイッチで遊べるという絶大なアドバンテージがあるので、お子様におすすめしやすいです。一方で、残念な事に Mac 版が存在しないという欠点があります。という事でマイクラ統合版のアドオン開発には Windows 機が必須となります。Mac に慣れた自分にはこれが一番キツイが仕方がない。。。

一般に、マイクラアドオンというとマイクラ統合版のアドオンを指します。Java 版の拡張機能は Mod と言って完全に別の仕組みです。

アドオン開発の公式サイトは [マインクラフト クリエーター](https://www.minecraft.net/ja-jp/creator) です。Microsoft らしい素晴らしい参考資料ですが、中身は英語なので子供には難しいかも知れません。

## サードパーティーのツールによるアドオン開発

アドオン開発には様々なサードパーティーツールが存在します。特に公式サイトで紹介されている [Blockbench](https://blockbench.net/) の Plugin を使えば、小学生でも簡単にアドオンを作成する事ができます。英語ですが [Getting Started with Minecraft Entity Wizard](https://learn.microsoft.com/en-us/minecraft/creator/documents/minecraftentitywizard) に解説があります。BlockBench を使えば、既存のマイクラのモブを元にスキンを変えたり動きを変えたり簡単にできます。例えば空を飛ぶニワトリとかを作れます。

ただ、Blockbench の Plugin だけでは色々機能が不足していて、例えば作ったアドオンを Realms で共有するのが子供には難しいです。Blockbench の本来の目的は低ポリゴンの 3Dモデルを作る事らしいので、Blockbench とほかのツールを組み合わせる必要があるのではないかと思っています。いくつかのツールを紹介します。

* [Blockbench](https://www.blockbench.net/)
    * 本家でも紹介されているローポリモデリングツール。Plugin で簡単にアドオンを作成できる。Web 版もある: https://web.blockbench.net/
* [MCreator](https://mcreator.net/)
    * Java 版の Mod 作成を GUI で行うツールらしい。最近統合版 Add-on にも対応したらしい。
* [Novaskin](https://minecraft.novaskin.me/)
    * Web でスキンの作成ができる。
* [SNOWSTORM](https://snowstorm.app/)
    * パーティクルを作成するツール
* [Mine-imator](https://www.mineimator.com/)
    * アドオン開発とは関係ないですが、マイクラっぽいアニメを作るツールらしい。

## 勉強の流れ

やみくもに試行錯誤を繰り返した結果、以下の二つの作業を平行して進める必要があるらしいと分かってきました。

* [Creator Learning Journey](https://learn.microsoft.com/en-us/minecraft/creator/documents/learningjourneyguide?view=minecraft-bedrock-stable) を元にまじめにアドオン開発を学ぶ。
    * アドオンの中身は zip で固めた json ファイルと画像などのリソースファイルなどです。まじめなアドオン開発とは、VisualStudio Code などでこれらを作成する事です。
    * 小学生にはまだこの方法は難しいので、サードパーティのツールを使わせる事にします。
    * ただ、サードパーティのツールはまじめなアドオン開発の知識を前提としているので、まじめなアドオン開発の知識は避けて通れないみたいです。
* サードパーティツールの使い方を学ぶ。
    * VisualStudio Code によるアドオンの直接開発は小学生には難しいので、子供にはサードパーティツールを組み合わせてアドオンを作ってもらいます。
    * 必要に応じて、ツールの拡張や改造を行います。

## 目次

記事が増えるたびにここに追記する予定です。

* [マインクラフト2: Creator Learning Journey を眺める。](https://propella.hatenablog.com/entry/2024/07/08/222335)
