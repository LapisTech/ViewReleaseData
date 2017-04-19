# ViewReleaseData

GitHubのAPIを使って、GitHub Releasesにアップしたバイナリがどれくらいダウンロードされているかを調べるサイトです。

## 使い方

* http://lapis.tech/ViewReleaseData/ にアクセスする。
* 調べたいGitHub Releasesを持つリポジトリのアカウント名とリポジトリ名と自分のアクセストークンを入力する。
    * アカウント名は個人アカウントならそのままの意味だが、組織の場合は組織の名前になる。
        * 例えばLapisTechは組織なので、LapisTech管理のリポジトリはLapisTechを指定する。
        * とりあえずリポジトリを持っているアカウントの名前。
    * リポジトリに関しては自分がその権限とか持ってないとだめなんじゃないかなぁ？多分。
    * アクセストークンは特に権限が必要ない。詳しくは下。
* ボタンを押すと取得してくれる。

## アクセストークンの取得

`Home` -> `Setting` -> `Developer settings` -> `Personal access tokens` -> `Generate new token`

特に何も指定せずそのまま作れば大丈夫。

## URLで初期入力

以下のようにGETパラメーターを与えると、初めから入力欄に値を入れてくれます。

http://lapis.tech/ViewReleaseData/?account=アカウント名&repository=リポジトリ名&token=アクセストークン

# 基本原理

以下APIをJavaScriptで叩いて調べてるだけ。

```
https://api.github.com/repos/アカウント名/リポジトリ名/releases?access_token=アクセストークン
```

プログラマーならこれ見れば分かるはず。

# その他

利用者のデータは保存していません。ソース見れば分かります。

サーバーもGitHub Pagesなので、特に何かできるわけではありません。

が、これを使う以上アクセストークンに変な権限を持たせないようにしておきましょう。
