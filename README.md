# React my Tutorial
Repository for React learning 

---

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [React my Tutorial](#react-my-tutorial)
- [References](#references)
- [Develop Environment](#develop-environment)
  - [Ubuntu18.04 LTS](#ubuntu1804-lts)
  - [curl (60) エラー発生時の対処](#curl-60-エラー発生時の対処)
  - [VS Code Debugger設定](#vs-code-debugger設定)
- [Start React Application](#start-react-application)

<!-- /code_chunk_output -->

---

# References

[Getting Started – React](https://reactjs.org/docs/getting-started.html)


# Develop Environment

Visual Studio Codeで開発環境を構築する

- [React JavaScript Tutorial in Visual Studio Code](https://code.visualstudio.com/docs/nodejs/reactjs-tutorial)
- [Download | Node.js](https://nodejs.org/en/download/)
- [tj/n: Node version management](https://github.com/tj/n)
- [Debug Browser Apps using Visual Studio Code](https://code.visualstudio.com/docs/nodejs/browser-debugging)

## Ubuntu18.04 LTS

- 環境：　`Linux 18.04 LTS (x64)`

- 方法：　[n package](https://github.com/tj/n)を使ってインストール

- メリット：
  - 最新バージョンの導入が容易
  - nodejsのバージョン管理が容易


コマンドだけ記載（詳細は下記サイトを確認）
[Ubuntuに最新のNode.jsを難なくインストールする - Qiita](https://qiita.com/seibe/items/36cef7df85fe2cefa3ea)
```bash
$ sudo apt install -y nodejs npm
$ sudo npm install n -g
/usr/local/bin/n -> /usr/local/lib/node_modules/n/bin/n
/usr/local/lib
└── n@8.0.2 
$ sudo n stable
$ sudo apt purge -y nodejs npm # 最初に入れた古い nodejs, npm は消しておく
$ exec $SHELL -l # ターミナルを再起動でいい
$ node -v
v16.14.0
```

## curl (60) エラー発生時の対処

**エラー内容**

```bash
$ sudo n stable
curl: (60) Cert verify failed: BADCERT_NOT_TRUSTED
More details here: https://curl.haxx.se/docs/sslcerts.html

curl failed to verify the legitimacy of the server and therefore could not
establish a secure connection to it. To learn more about this situation and
how to fix it, please visit the web page mentioned above.

  Error: failed to download version index (https://nodejs.org/dist/index.tab)
```

**対処**

[SSL証明書](https://www.rworks.jp/system/system-column/sys-entry/21283/)の検証ができずにエラーが出ているようなので、`--insecure`オプションでそのエラーを無視してあげれば通ります（[参考サイト](https://linuxfan.info/curl-insecure)）。

```bash
$ sudo n stable --insecure
```

## VS Code Debugger設定

`index.js`を開いて`Ctrl+Shift+D` or `F5`キーで`launch.json`ファイルを作成します。
デフォルトだと`url`のポートが`8080`なので`3000`に変えておきます。
私はChrome派なので、`type`を`pwa-chrome`にしています。

```json
// launch.json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "pwa-chrome",
            "request": "launch",
            "name": "Launch Chrome against localhost",
            "url": "http://localhost:3000",
            "webRoot": "${workspaceFolder}"
        }
    ]
}
```


# Start React Application

```bash
$ npx create-react-app my-app
```

こんな感じのファイル構成で雛形が作成されます

```bash
my-app
    ├── README.md
    ├── node_modules
    ├── package-lock.json
    ├── package.json
    ├── public
    └── src
```










