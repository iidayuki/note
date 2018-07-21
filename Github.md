# Githubでよく使うコマンドまとめ


## git status
  * リポジトリの状態を確認
　* 現在のブランチの名称や、追加・変更されたファイルやディレクトリの一覧を表示  

    git status
    
## git add
   * ファイルやディレクトリをインデックスに追加
   * 追加するときの[file_pattern]には、ファイル名やディレクトリ名を直接している他に、  「*.txt」のように、ワイルドカードで複数対象を指定することも可能
   
    git add [file_pattern]

## git commit
   * インデックスに追加されたファイルやフォルダの変更をリポジトリに書き込む
   * オプションを指定しないでこのコマンドを実行すると、コミットメッセージを記述するためのエディタが起動
   * エディタの使い方は異なるので、簡単にメッセージを指定するには-mオプションを付けた後にダブルクォーテーションで囲ったメッセージを指定
   * また、-aオプションを指定すると、変更されたファイルを検出してインデックスに追加する動作も同時に行う
   
    git commit -am "A first commit"
    
## git branch
   * ブランチに対して各種操作を行う
     * git branch [branch-name]：ブランチの作成
     * git branch：ブランチの一覧表示
     * git branch –d [branch-name]：指定したブランチを削除
     
## git checkout
   * ローカルリポジトリのブランチを切り替える
   
    git checkout [branch-name]
 
## git log
   * ローカルリポジトリのコミット履歴を閲覧
   * -nオプションで履歴の表示数を指定可能
   
    git log –n 10
    
## git grep
   * リポジトリのファイルの内容から検索したいとき
   * 特定の語句が含まれているファイルを検索し、そのファイルのどこに語句が含まれているかを調べる
   
    git grep "検索単語"
    
## git clone 
   * 既存のリモートリポジトリをローカルに落とす
   * 例えば、GitHubに公開されているリポジトリを自分のコンピュータへ落とすときに使う
   
    git clone [url]

## git remote
   * リモートリポジトリを操作するために使うコマンドで下記のように使う
     * git remote：リモートリポジトリの名称一覧を表示
     * git remote -v：リモートリポジトリの詳細一覧を表示
     * git remote add [name] [url]：リモートリポジトリを追加
     * git remote rm [name]：リモートリポジトリを削除
     
## git reset
   * ローカルリポジトリのコミットを取り消す
   * 間違えてコミットしたり、修正漏れがあったときに使う

     git reset –soft HEAD^

## git marge
   * 現在のブランチに対して、他のブランチで行った変更を取り込む
   * 以下の例では、ブランチbug-fixをmasterブランチにマージする
   
    git checkout master
    git merge bug-fix
    
## git pull
   * リモートブランチの変更を取り込む
   * 以下の例では、ローカルリポジトリのmasterブランチにリモートリポジトリoriginのmasterブランチを取り込む
   
    git checkout master
    git pull origin master
    
    
   
