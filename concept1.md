## Forkとは

ForkはGitHubに実装されている機能で、便利なためにGitHubだけではなく、GitLabやBitBucketなどにも採用されている機能です。

Forkとは、簡単にいうとGitHub上のリポジトリのコピーを作成することです。

オープンソースのプロジェクトや、CodeGritの生徒用のリポジトリには、通常許可がないと直接変更を加えることが出来ないようになっています。

そこでForkを利用すると、そのリポジトリを自分のリポジトリとして扱えるので変更を保存することが出来るようになります。

## リポジトリをForkする

今回はForkの練習用に作成した以下のリポジトリを使ってみましょう。

- [codegrit-jp-students/fork-practice](https://github.com/codegrit-jp-students/fork-practice)

![Fork1](./images/fork-practice-1.png)

リポジトリのページの右上にFork(画像参照)という文字があるのでこちらをクリックしてください。

すると、新しい画面が出てきてユーザーを選ぶ画面が出てきますので、自分のアカウントを選んでください。

すると、リポジトリが自分のリポジトリとしてフォークされます。

![Fork2](./images/fork-practice-2.png)

## `git clone`でローカル上にリポジトリをダウンロードする

次に`git clone`というコマンドを利用してフォークしたリポジトリをローカル上にダウンロードしましょう。

```bash
$ git clone https://github.com/ユーザー名/fork-practice.git
Cloning into 'fork-practice'...
remote: Counting objects: 6, done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 6 (delta 0), reused 6 (delta 0), pack-reused 0
Unpacking objects: 100% (6/6), done.
```

すると上記のようなメッセージが出て、無事にリポジトリがローカル上にクローンされるはずです。

## フォーク先のリポジトリに変更を加える

では、次に先ほどクローンしたリポジトリに変更を加えてみましょう。変更内容はなんでもかまいません。

これをいつもどおりの流れでpushします。

```bash
$ git add .
$ git commit -m "update README.md"
$ git push origin master
Counting objects: 3, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 417 bytes | 417.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/ユーザー名/fork-practice.git
   41ea7c4..7de423a  master -> master
```

## フォーク元のリポジトリにPull Requestを送信する

フォーク先に無事変更が反映されたら、フォーク元のリポジトリへPull Requestを送信します。

Pull Requestとは、この場合はフォーク先で加えた変更をフォーク元に反映してくださいとお願いすることとなります。

フォーク元の管理者は、Pull Request上の変更の内容やメッセージを見て、変更を承認するかどうか決めることが出来ます。

承認された場合は、チームメンバーはその変更を`git pull`でローカルリポジトリに反映することになります。そのために**Pull Request**という名前がついています。

Pull Requestを行うには、まずフォーク先のリポジトリのページで"New pull request"というボタンをクリックします。(画像参照)

![Pull Request1](./images/fork-practice-3.png)

次のページでは、変更内容を再度確認出来ます。問題なければ左上の"Create pull request"というボタンをクリックします。

![Pull Request2](./images/pull-request-2.png)

すると以下のようにコメントを入れることの出来る画面が出てきます。

![Pull Request3](./images/pull-request-3.png)

タイトルとコメントを加えて大丈夫なら再度右下の"Create pull request"ボタンをクリックします。

すると、以下の画像のようにフォーク元の開発者がコメントを行ったり、リクエスト内容を承認するか選べるページが作成されます。

![Pull Request4](./images/pull-request-4.png)