# Github Pages Rewrite

## Github Pages で mod_rewrite のようなパーマリンクでの遷移を可能にします。

このリポジトリは実際に [Github Pages](https://postease-cms.github.io/ghp-rewrite) でホスティングしています。

### パーマリンク実現の仕組み

javascript のみを利用して実現しています。  
jekyll の redirect_from などの機能は一切使用していません。  
Apache や nginx 環境における rewrite と同ソースで運用が可能です。

1. パーマリンクによる無効なURLを一旦 404.html で受ける（Github Pages のデフォルトの仕様）。</li>
2. 404.html に仕込んだ javascript で、クエリストリング付きの有効なURLに変換して目的のページにリダイレクト。</li>
3. リダイレクトされた目的のページで historyAPI の replaceState を使って、URLを最初にリクエストされたパーマリンクに変換</li>

