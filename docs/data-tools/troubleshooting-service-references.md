---
title: "Troubleshooting Service References | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther"
  - "msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo"
  - "msvse_wcf.Err.ErrorOnOK"
  - "msvse_wcf.cfg.ConfigurationErrorsException"
helpviewer_keywords: 
  - "service references [Visual Studio], troubleshooting"
  - "WCF services, troubleshooting"
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 22
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Troubleshooting Service References
ここでは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] 参照または [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] 参照を使用するときに発生する可能性のある一般的な問題について説明します。  
  
## サービスからデータを返すときのエラー  
 サービスから `DataSet` または `DataTable` を返す場合に、"受信メッセージの最大メッセージ サイズ クォータが超過されました" という例外が発生することがあります。  既定では、サービス拒否攻撃を受けるリスクを低減するために、一部のバインディングの `MaxReceivedMessageSize` プロパティが比較的小さい値に設定されています。  この値を大きくすると、例外の発生を避けることができます。  詳細については、「<xref:System.ServiceModel.BasicHttpBinding.MaxReceivedMessageSize%2A>」を参照してください。  
  
 このエラーを修復するには、次の処理を行います。  
  
1.  **ソリューション エクスプローラー**で、app.config ファイルをダブルクリックして開きます。  
  
2.  `MaxReceivedMessageSize` プロパティを探して、大きい値に変更します。  
  
## \[マイ ソリューション\] でサービスが見つからない  
 **\[サービス参照の追加\]** ダイアログ ボックスの **\[探索\]** ボタンをクリックしても、ソリューション内の 1 つ以上の WCF サービス ライブラリ プロジェクトがサービスの一覧に表示されないことがあります。  これは、ソリューションにサービス ライブラリが追加されただけで、まだコンパイルされていない場合に発生することがあります。  
  
 このエラーを修復するには、次の処理を行います。  
  
-   **ソリューション エクスプローラー**で WCF サービス ライブラリ プロジェクトを右クリックし、**\[ビルド\]** をクリックします。  
  
## リモート デスクトップ経由でサービスにアクセスするときのエラー  
 Web ホストされた WCF サービスにユーザーがリモート デスクトップ接続経由でアクセスしたとき、そのユーザーに管理者権限がないと、NTLM 認証が使用されます。  ユーザーが管理者権限を持たない場合、このユーザーに対して次のようなメッセージが出される場合があります。"この HTTP 要求は、クライアントの認証方式 '匿名' では承認されません。  サーバーから受信した認証ヘッダーは "NTLM" でした。"  
  
 このエラーを修復するには、次の処理を行います。  
  
1.  Web サイト プロジェクトで、**\[プロパティ\]** ページを開きます。  
  
2.  **\[開始オプション\]** タブの **\[NTLM 認証\]** チェック ボックスをオフにします。  
  
    > [!NOTE]
    >  NTLM 認証をオフにするのは、WCF サービスだけを含む Web サイトの場合に限定してください。  WCF サービスのセキュリティは、web.config ファイルの構成によって管理されます。  そのため、NTLM 認証は必要ありません。  
  
 詳細については、「[例外のトラブルシューティング : System.ServiceModel.Security.MessageSecurityException](../misc/troubleshooting-exceptions-system-servicemodel-security-messagesecurityexception.md)」を参照してください。  
  
## \[生成されたクラスのアクセス レベル\] の設定に効果がない  
 **\[サービス参照の構成\]** ダイアログ ボックスの **\[生成されたクラスのアクセス レベル\]** オプションを **\[内部\]** または **\[Friend\]** に設定しても、その設定が機能しない場合があります。  ダイアログ ボックスでこのオプションが設定されているように見えても、生成されるサポート クラスのアクセス レベルは `Public` になります。  
  
 これは、<xref:System.Xml.Serialization.XmlSerializer> を使用してシリアル化された型など、特定の型に対する既知の制限事項です。  
  
## デバッグ サービス コードのエラー  
 WCF サービスのコードにクライアント コードからステップ インした場合に、シンボルが見つからないことを示すエラーが返されることがあります。  これは、ソリューションの一部であったサービスがソリューションから移動または削除されると発生します。  
  
 現在のソリューションの一部である WCF サービスに最初に参照を追加したときに、サービス プロジェクトとサービス クライアント プロジェクトの間に明示的なビルド依存関係が追加されます。  これにより、クライアントが常に最新のサービス バイナリにアクセスすることが保証されます。これは、クライアント コードからサービス コードにステップ インするなどのデバッグ シナリオにおいて特に重要です。  
  
 サービス プロジェクトがソリューションから削除されると、明示的なビルド依存関係が無効になります。  Visual Studio では、必要に応じてサービス プロジェクトが再度ビルドされることが保証されなくなりました。  
  
 このエラーを修復するには、次の手順に従ってサービス プロジェクトを手動で再度ビルドする必要があります。  
  
1.  **\[ツール\]** メニューの **\[オプション\]** をクリックします。  
  
2.  **\[オプション\]** ダイアログ ボックスで、**\[プロジェクトおよびソリューション\]** を展開し、**\[全般\]** をクリックします。  
  
3.  **\[ビルド構成の詳細を表示\]** チェック ボックスがオンになっていることを確認して **\[OK\]** をクリックします。  
  
4.  WCF サービス プロジェクトを読み込みます。  詳細については、「[方法 : 複数のプロジェクトから成るソリューションを作成する](http://msdn.microsoft.com/ja-jp/02ecd6dd-0114-46fe-b335-ba9c5e3020d6)」を参照してください。  
  
5.  **\[構成マネージャー\]** ダイアログ ボックスで、**\[アクティブ ソリューション構成\]** を **\[デバッグ\]** に設定します。  詳細については、「[方法 : 構成を作成および編集する](../ide/how-to-create-and-edit-configurations.md)」を参照してください。  
  
6.  **ソリューション エクスプローラー**で WCF サービス プロジェクトを選択します。  
  
7.  **\[ビルド\]** メニューの **\[リビルド\]** をクリックして、WCF サービス プロジェクトを再度ビルドします。  
  
## WCF Data Services がブラウザーに表示されない  
 [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] のデータの XML 表記を表示しようとすると、Internet Explorer はこのデータを RSS フィードと間違って解釈します。  RSS フィードを表示するオプションが無効になっていることを確認してください。  
  
 このエラーを修復するには、RSS フィードを無効にします。  
  
1.  Internet Explorer で、**\[ツール\]** メニューの **\[インターネット オプション\]** をクリックします。  
  
2.  **\[コンテンツ\]** タブの **\[フィード\]** で、**\[設定\]** をクリックします。  
  
3.  **\[フィードの設定\]** ダイアログ ボックスで、**\[フィードの読み取りビューを有効にする\]** チェック ボックスをオフにし、**\[OK\]** をクリックします。  
  
4.  **\[OK\]** をクリックして、**\[インターネット オプション\]** ダイアログ ボックスを閉じます。  
  
## 参照  
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Consuming ASMX and WCF Services Sample](http://msdn.microsoft.com/ja-jp/788ddf2c-2ac1-416b-8789-2fbb1e29b8fe)