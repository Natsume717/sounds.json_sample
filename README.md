# sounds.json_sample
音声ファイルを追加するためのsounds.jsonなどに関するデータパックサンプルになります。

詳しくはブログ記事『[【マイクラ】効果音を追加するにはsounds.jsonを作る！](https://natsumake.com/sounds_json/)』を参考にしてください。

<h3>使い方</h3>
まずはリソースパックとして、Minecraftに導入してください。

読み込み後、以下のコマンド

```/playsound custom:handcrap.01 master @a ~ ~ ~ 1 1 1```

```/playsound custom:handcrap.02 master @a ~ ~ ~ 1 1 1```

```/playsound custom:handcrap.03 master @a ~ ~ ~ 1 1 1```

を実行することができるようになります。

それぞれ私が録音した手を叩いた音が流れます。<br>
3つ目のcustom:handcrap.03は01と02がランダムに鳴るようになっているものです。

<h3>簡単な解説</h3>
ブログ記事で解説していない点として

+ handcrap.02が参照する音声ファイルの格納場所
+ handcrap.03の指示

について解説します。

<h4>handcrap.02が参照する音声ファイルの格納場所</h4>

これはsoundsフォルダ下にフォルダを作成し、そこへoggファイルを格納しただけです。<br>
実際、ファイル位置の指示が```custom:custom_folder/handcrap_02```とcustom_folderの下階層だということがうかがえます。

<h4>handcrap.03の指示</h4>

こちらについては、複数のファイルを参照するよう指示することで実現可能です。

```  "handcrap.03": {
    "replace": true,
    "sounds": [
      {
        "name": "random.burp",
        "type": "event",
        "weight": 600,
        "stream": true,
        "attenuation_distance":16,
        "preload":false,
        "volume":1.0,
        "pitch":1.0
      },
      "custom:handcrap_01",
      "custom:custom_folder/handcrap_02"
    ]
  }
```
後半部分に2つのファイルを参照しようとしていることが分かりますね。<br>
詳細についてはまだ検証中の部分でもあります。<br>
（音声ごとに選択される確率を変更することが出来るのかなど）
