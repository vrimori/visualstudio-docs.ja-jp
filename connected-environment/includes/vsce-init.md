## <a name="initialize-code-for-docker-and-kubernetes-development"></a>Docker と Kubernetes 開発でコードを初期化する
ここまでで、ローカルで実行できる基本的な Web アプリが用意されました。 次にこれをコンテナー化します。アプリのコンテナーとそれを Kubernetes に展開する方法を定義するアセットを作成します。 Connected Environment を利用することでこの作業は簡単になります。 

1. VS Code を起動し、`webfrontend` フォルダーを開きます。 (デバッグ アセットの追加やプロジェクトの復元など、既定のプロンプトはすべて無視できます。)
1. VS Code で統合端末を開きます (**[表示] の [統合端末]** メニューを利用します)。
1. 次のコマンドを実行します (**webfrontend** が現在のフォルダーになっていることを確認してください)。

```cmd
vsce init --public
```

Connected Environment CLI の ```init``` コマンドによって、Docker アセットと Kubernetes アセットが既定の設定で生成されます。
* `./Dockerfile` は、アプリのコンテナー イメージと、コンテナー内でソース コードを構築し、実行するしくみを表すものです。
* `./charts/webfrontend` の下にある [Helm チャート](https://docs.helm.sh)は、Kubernetes にコンテナーを展開するしくみを表すものです。

今のところ、これらのファイルの中身をすべて理解する必要はありません。 ただし、**Kubernetes と Docker の同じ Configuration-as-Code (コードとしての構成) アセットを開発から運用まで利用できること、したがって、さまざまな環境の間で整合性が良くなるということ**は指摘に値します。
 
`./vsce.yaml` という名前のファイルも `init` コマンドで生成されます。これは Connected Environment の構成ファイルです。 これは Docker と Kubernetes の成果物を追加の構成で補完するものであり、Azure で繰り返し開発が可能になります。 たとえば、既定の Helm チャートではパブリック エンドポイントが公開されません。 ただし、開発中、パブリック エンドポイントを一時的に公開すると便利な場合があります。たとえば、モバイル デバイスや webhook URL からコードをテストできます。 `init --public` を使用して作成された vsce.yaml ファイルは Helm の既定パラメーターをオーバーライドし、開発期間だけパブリック エンドポイントを公開します。
