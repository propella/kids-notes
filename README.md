# 子供用 PC 雑記帳

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
