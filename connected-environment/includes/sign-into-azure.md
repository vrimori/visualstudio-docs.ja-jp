## <a name="sign-in-to-azure"></a>Azure にサインインする
開発環境を作成するには Azure にサインインする必要があります。 端末ウィンドウに次のコマンドを入力します。
```cmd
az login
```

> [!Note]
> Azure サブスクリプションをお持ちでなければ、[無料のアカウント](https://azure.microsoft.com/free)を作成できます。

### <a name="if-you-have-multiple-azure-subscriptions"></a>複数の Azure サブスクリプションをお持ちの場合...
次を実行すると、自分のサブスクリプションを表示できます。 
```cmd
az account list
```
JSON 出力に `isDefault: true` が表示されたサブスクリプションを見つけます。
これが使用するサブスクリプションではない場合、既定のサブスクリプションを変更できます。
```cmd
az account set --subscription <subscription ID>
```
