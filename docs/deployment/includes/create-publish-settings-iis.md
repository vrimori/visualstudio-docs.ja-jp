
1. UI で更新された構成オプションを表示する、IIS 管理コンソールを閉じてから開き。

1. IIS を右クリックし、**既定の Web サイト**、選択**展開** > **Web 配置をパブリッシング**です。

    ![Web 配置の構成を構成します。](../../deployment/media/tutorial-configure-web-deploy-publishing.png)

1. **Web 配置をパブリッシング** ダイアログ ボックスで、設定を確認します。

1. をクリックして**セットアップ**です。

    **結果**パネルで、アクセス権をその出力を示しますが指定されたユーザーに付与されますファイルが、 *.publishsettings*ダイアログ ボックスで表示されている場所でファイル拡張子が生成されましたボックスです。

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

    Windows Server と IIS の構成によっては、XML ファイル内の別の値を表示します。 次に、いくつかの詳細が表示される値を示します。

    * *Msdeploy.axd*で参照されているファイル、`publishUrl`属性は Web Deploy を動的に生成された HTTP ハンドラー ファイル。 (テスト目的で`http://myhostname:8172`通常でも同じです)。
    * `publishUrl`ポートはポート 8172、Web 配置の既定値に設定します。
    * `destinationAppUrl`ポートはポート 80、IIS の既定値に設定します。
    * (後の手順) でホスト名を使用して Visual Studio でリモート ホストに接続できない場合は、ホスト名の代わりに IP アドレスをテストします。

    > [!NOTE]
    > Azure VM で実行されている IIS に発行する場合は、ネットワーク セキュリティ グループに属する Web デプロイおよび IIS のポートを開く必要があります。 詳細については、次を参照してください。[実行 IIS をインストールして](/azure/virtual-machines/windows/quick-create-portal#open-port-80-for-web-traffic)です。

1. このファイルを Visual Studio が実行されているコンピューターにコピーします。
