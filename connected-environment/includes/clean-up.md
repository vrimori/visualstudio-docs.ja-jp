## <a name="clean-up"></a>クリーンアップ
Azure で Connected Environment を完全に、その中で実行されているすべてのサービスを含めて削除するには、`vsce env rm` コマンドを使用します。 この操作は元に戻せないことにご留意ください。

次のサンプルでは、アクティブな Azure サブスクリプションの Connected Environment が一覧表示され、リソース グループ 'myenv-rg' にある 'myenv' という名前の環境が削除されます。

```cmd
vsce env list
vsce env rm --name myenv --resource-group myenv-rg
```

