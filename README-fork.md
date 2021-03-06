# Git fork

コミット権限を持っていないリポジトリのソースを修正する必要がある場合には、``fork``を使います。
リポジトリを``fork``すると、元のリポジトリと同じリポジトリを作成することができます。
単なるコピーと違い、下記のことが可能となります。

- ``fork``したあとに発生したコミットの取り込む
- 作成したコミットの取り込みを依頼する

説明では、下記の用語を使います。

| 用語         | 説明               |
|:-------------|:-------------------|
| upstream     | fork元のリポジトリ |
| Pull Request | 修正の取り込み依頼 |

## 手順

``fork``の事前準備と日々の作業は、以下の通りです。

- 事前準備
  - リポジトリをfork
  - リポジトリのcloneとupstreamの設定
- 日々の作業
  - upstreamの修正取り込み
  - upstreamへの修正の取り込み依頼(Pull Request)

## 事前準備

``fork``を使うための事前準備を説明します。

## リポジトリをfork

ブラウザで``upstream``のリポジトリにアクセスして``fork``ボタンを押すとリポジトリが作成されます。
``upstream``の開発者は、``fork``された数が表示されるので``fork``されたことが分かります。

## リポジトリのcloneとupstreamの設定

``fork``したリポジトリをクローンします。

```
git clone <forkしたリポジトリのURL>
cd <cloneされたディレクトリ>
```

次にupstreamを設定します。

```
git remote add upstream <fork元のリポジトリのURL>
```

設定した内容は、下記で確認できます。

```
$ git remote -v
origin          <forkしたリポジトリのURL> (fetch)
origin          <forkしたリポジトリのURL> (push)
upstream        <fork元のリポジトリのURL> (fetch)
upstream        <fork元のリポジトリのURL> (push)
$
```

これで、準備完了です。

## upstreamの修正取り込み

次のコマンドで``upstream``の``master``ブランチの修正を現在のブランチに取り込みます。

```
git fetch upstream
git merge upstream/master
```

## upstreamへの修正の取り込み依頼(Pull Request)

``master``ブランチから作業用のブランチを作成して修正を行います。

```
git checkout -b work
... 何か変更 ...
git commit -a -m "コミットメッセージ"
git push origin work
```

ブラウザからブランチを選択して``Pull Request``を作成します。
``Pull Request``は、``fork``先のブランチから``upstream``の``master``ブランチへの``Pull Request``になります。

``upstream``側で``Pull Request``がレビューされます

以上
