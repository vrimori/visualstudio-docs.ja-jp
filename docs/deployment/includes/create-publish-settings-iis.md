
1. UI の更新された構成オプションを表示する、IIS 管理コンソールを閉じてから。

1. IIS を右クリックし、**既定の Web サイト**、選択**デプロイ** > **Web 配置発行の構成**します。

    ![Web 配置の構成を構成します。](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. **Web 配置発行の構成** ダイアログ ボックスで、設定を確認します。

1. クリックして**セットアップ**します。

    **結果**パネルで、アクセス権をその出力を示しますが、指定したユーザーに付与されますを持つファイルを *.publishsettings*ダイアログ ボックスで示されている場所にファイル拡張子が生成されましたボックス。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <publishData>
      <publishProfile
        publishUrl="https://myhostname:8172/msdeploy.axd"
        msdeploySite="Default Web Site"
        destinationAppUrl="http://myhostname:80/"
        mySQLDBConnectionString=""
        SQLServerDBConnectionString=""
        profileName="Default Settings"
        publishMethod="MSDeploy"
        userName="myhostname\myusername" />
    </publishData>
    ```

    Windows Server と IIS の構成によっては、XML ファイル内のさまざまな値参照してください。 いくつかの詳細については、表示される値を次に示します。

    * *Msdeploy.axd*ファイルで参照されている、`publishUrl`属性は、Web デプロイのために動的に生成される HTTP ハンドラー ファイル。 (テスト目的で、`http://myhostname:8172`も機能します)。
    * `publishUrl`ポートはポート 8172、Web 配置の既定値に設定します。
    * `destinationAppUrl`ポートはポート 80、IIS の既定値に設定します。
    * (後の手順) でホスト名を使用して Visual Studio でのリモート ホストに接続されない場合は、ホスト名の代わりに IP アドレスをテストします。

    > [!NOTE]
    > Azure VM で実行されている IIS に発行する場合は、ネットワーク セキュリティ グループで Web デプロイおよび IIS のポートを開く必要があります。 詳細については、次を参照してください。[実行 IIS をインストールして](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic)します。

1. このファイルを Visual Studio を実行しているコンピューターにコピーします。
