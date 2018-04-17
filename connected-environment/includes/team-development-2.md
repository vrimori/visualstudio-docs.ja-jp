2. F5 を押し (あるいは端末ウィンドウに「`vsce up`」と入力し)、サービスを実行します。 これで、新しく選択したスペース `scott` で自動的にサービスが実行されます。 
1. `vsce list` をもう一度実行し、これを確定できます。 最初に、`mywebapi` のインスタンスが `scott` スペースで実行中であることを確認できます (`mainline` で実行されているバージョンは引き続き実行されていますが、一覧にはありません)。 次に、`webfrontend` のアクセス ポイント URL の先頭に "scott-" というテキストが付けられます。 この URL は `scott` スペースに固有です。"scott URL" に送信された要求は最初に `scott` スペースに進もうとして失敗し、`mainline` スペースのサービスにフォールバックします。

```
Name         Space     Chart              Ports   Updated     Access Points
-----------  --------  -----------------  ------  ----------  -------------
mywebapi     scott     mywebapi-0.1.0     80/TCP  15s ago     http://localhost:61466
webfrontend  mainline  webfrontend-0.1.0  80/TCP  5h ago      https://scott-webfrontend-contosodev.vsce.io
```

![](../media/space-routing.png)

Connected Environment のこの組み込み機能を使用すれば、共有環境でコードをエンドツーエンドでテストできます。各開発者が自分のスペースでサービスの完全なスタックを再作成する必要はありません。 このガイドの前の手順で示したように、このルーティングでは伝達ヘッダーをアプリ コードで転送する必要があることに注意してください。

## <a name="test-code-in-a-space"></a>スペースでコードをテストする
`webfrontend` との連動で新しいバージョンの `mywebapi` をテストするには、ブラウザーを起動して webfrontend のパブリック アクセス ポイント URL を開き、[バージョン情報] ページに移動します。 新しいメッセージが表示されるはずです。

URL から "scott-" の部分を削除し、ブラウザーを更新します。 (`mainline` で実行されている `mywebapi` バージョンで示される) 以前の動作を確認できるはずです。