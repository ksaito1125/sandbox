# Gitの検証用リポジトリ

このリポジトリは、Gitの検証用です。

## Git fork

git forkを使ってコミット権限のないリポジトリのソースを取得しupstreamの変更を継続的に取り込む手順です。

### 事前準備

* オリジナルのリポジトリをforkする
* upstreamを設定する

### オリジナルのリポジトリの変更を取り込む

forkしたリポジトリで下記を実行します。

```
git fetch upstream
git merge upstream master
```

### forkしたリポジトリのパッチを取り込む

作業用ブランチの取り込みとupstreamでのPRなどによるmasterへの取り込み

```
git checkout -b work
git commit -a
git push upstream work
```

```
git fetch
git merge origin/work
```

以上
