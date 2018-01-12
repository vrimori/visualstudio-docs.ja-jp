---
title: "Visual Studio での SharePoint ツールの拡張機能のデバッグ |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, debugging extensions
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: ead91600a4f62899f2b7182f2d7248afa77651d3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="debugging-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Visual Studio での SharePoint ツールの拡張機能のデバッグ
  Visual Studio の実験用インスタンスまたは通常のインスタンスで、SharePoint ツールの拡張機能をデバッグできます。 拡張機能の動作をトラブルシューティングする必要がある場合は、レジストリ値を変更して、追加のエラー情報を表示し、Visual Studio での SharePoint コマンドの実行方法を構成することもできます。  
  
## <a name="debugging-extensions-in-the-experimental-instance-of-visual-studio"></a>Visual Studio の実験用インスタンスで拡張機能をデバッグする  
 Visual Studio SDK と呼ばれる、代替の Visual Studio インスタンスを提供するテストされていない拡張機能によって不慮の破損から Visual Studio 開発環境を保護するために、*実験用インスタンス*、使用することができますインストールして、拡張機能をテストします。 新しい拡張機能は Visual Studio の通常のインスタンスを使用して開発しますが、デバッグと実行は実験用インスタンスで行います。 詳細については、次を参照してください。 [、実験用インスタンス](/visualstudio/extensibility/the-experimental-instance)です。  
  
 VSIX プロジェクトを使用して拡張機能を配置し、その VSIX プロジェクトをソリューションのスタートアップ プロジェクトにする場合は、ソリューションをデバッグするときに、実験用インスタンスで拡張機能が自動的にインストールされて実行されます。 スタートアップ プロジェクトとは、複数のプロジェクトを含むソリューションをデバッグするときに開始されるプロジェクトです。 VSIX プロジェクトを使用して拡張機能を配置する方法の詳細については、次を参照してください。 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)です。  

 Visual Studio の実験用インスタンスでさまざまな種類の拡張機能をデバッグする方法を示す例については、次のチュートリアルを参照してください。  
  
-   [チュートリアル: SharePoint プロジェクト項目の種類の拡張](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [チュートリアル: 項目テンプレートに基づくカスタム動作プロジェクト項目の作成 (パート 1)](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [チュートリアル: SharePoint プロジェクトに対するカスタムの配置手順の作成](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [チュートリアル: サーバー エクスプローラーを拡張して Web パーツを表示する](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [チュートリアル: サーバー エクスプローラーの拡張機能から SharePoint クライアント オブジェクト モデルを呼び出す](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## <a name="debugging-extensions-in-the-regular-instance-of-visual-studio"></a>Visual Studio の通常のインスタンスで拡張機能をデバッグする  
 Visual Studio の通常のインスタンスで拡張機能プロジェクトをデバッグするには、まず、その拡張機能を通常のインスタンスにインストールします。 次に、デバッガーを Visual Studio の第 2 プロセスにアタッチします。 デバッグの完了後、拡張機能を削除して、開発用コンピューターに読み込まれないようにすることができます。  
  
#### <a name="to-install-the-extension"></a>拡張機能をインストールするには  
  
1.  Visual Studio のすべてのインスタンスを閉じます。  
  
2.  拡張機能プロジェクトのビルド出力フォルダーで探し、.vsix ファイルをダブルクリックして開くか、ショートカット メニューを開き、**開く**:  
  
3.  **Visual Studio 拡張機能インストーラー**  ダイアログ ボックスで、クリックして、拡張機能をインストールする Visual Studio のエディションを選択、**インストール**ボタンをクリックします。  
  
     Visual Studio では、拡張機能のファイルをインストール %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions に\\*作成者名*\\*拡張機能名*\\*バージョン*します。 このパスの最後の 3 つのフォルダーは、拡張機能の extension.vsixmanifest ファイル内の `Author`、`Name`、および `Version` の各要素から構築されます。  
  
4.  Visual Studio 拡張機能をインストールした後は、選択、**閉じる**ボタンをクリックします。  
  
#### <a name="to-debug-the-extension"></a>拡張機能をデバッグするには  
  
1.  管理者特権で Visual Studio を起動し、拡張機能プロジェクトを開きます。 次の手順として Visual Studio のこのインスタンスを参照してください、*最初インスタンス*です。  
  
2.  Visual Studio の別のインスタンスを管理者特権で起動します。 次の手順として Visual Studio のこのインスタンスを参照してください、 *2 番目のインスタンス*です。  
  
3.  Visual Studio の第 1 インスタンスに切り替えます。  
  
4.  メニュー バーで、次のように選択します。**デバッグ**、**プロセスにアタッチする**です。  
  
5.  **選択可能なプロセス**一覧で、devenv.exe を選択します。 これが、Visual Studio の第 2 インスタンスを表します。プロジェクトの拡張機能は、このインスタンスでデバッグすることになります。  
  
6.  選択、**アタッチ**ボタンをクリックします。  
  
     Visual Studio によって拡張機能プロジェクトがデバッグ モードで実行されます。  
  
7.  Visual Studio の第 2 インスタンスに切り替えます。  
  
8.  拡張機能を読み込む新しい SharePoint プロジェクトを作成します。 たとえば、リスト定義プロジェクト項目の拡張機能をデバッグしている場合は、作成、**リスト定義**プロジェクト。  
  
9. 拡張機能のコードのテストに必要な手順をすべて実行します。  
  
10. 拡張機能のデバッグが完了したら、Visual Studio の第 2 インスタンスを閉じます。  
  
#### <a name="to-remove-the-extension"></a>拡張機能を削除するには  
  
1.  Visual Studio で、メニュー バーで、選択**ツール**、**拡張機能と更新プログラム**です。  
  
     **[拡張機能と更新プログラム]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で、拡張機能の名前を選択し、、**アンインストール**ボタンをクリックします。  
  
3.  ダイアログ ボックスが表示されますが、選択、**はい**extension をアンインストールすることを確認するにはボタン。  
  
4.  選択、**今すぐ再起動**ボタンをクリックしてアンインストールを完了します。  
  
## <a name="debugging-sharepoint-commands"></a>SharePoint コマンドのデバッグ  
 SharePoint ツールの拡張機能に属している SharePoint コマンドをデバッグする場合は、vssphost4.exe プロセスにデバッガーをアタッチする必要があります。 これは、SharePoint コマンドを実行する 64 ビット ホスト プロセスです。 SharePoint コマンドと vssphost4.exe の詳細については、次を参照してください。[の SharePoint オブジェクト モデルを呼び出す](../sharepoint/calling-into-the-sharepoint-object-models.md)です。  
  
#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>vssphost4.exe プロセスにデバッガーをアタッチするには  
  
1.  前に説明した手順に従って、Visual Studio の実験用インスタンスまたは Visual Studio の通常のインスタンスで拡張機能のデバッグを開始します。  
  
2.  メニュー バーで、デバッガーを実行は、Visual Studio のインスタンスで**デバッグ**、**プロセスにアタッチする**です。  
  
3.  **選択可能なプロセス**一覧で、vssphost.exe を選択します。  
  
    > [!NOTE]  
    >  vssphost.exe が一覧に表示されない場合は、拡張機能を実行する Visual Studio のインスタンスで vssphost4.exe プロセスを開始する必要があります。 通常、そのためには、Visual Studio によって開発コンピューター上の SharePoint サイトに接続する操作を実行します。 下にあるサイト接続ノード (サイトの URL を表示するノード) を展開するときに、Visual Studio が vssphost4.exe を開始するなど、 **SharePoint 接続**内のノード、**サーバー エクスプ ローラー**ウィンドウ、またはときにします。など、特定の SharePoint プロジェクト項目の追加**リスト インスタンス**または**イベント レシーバー** SharePoint プロジェクトへの項目。  
  
4.  選択、**アタッチ**ボタンをクリックします。  
  
5.  デバッグ対象の Visual Studio のインスタンスで、コマンドの実行に必要な手順を実行します。  
  
## <a name="modifying-registry-values-to-help-debug-sharepoint-tools-extensions"></a>SharePoint ツールの拡張機能のデバッグが簡単になるようにレジストリ値を変更する  
 Visual Studio の SharePoint ツールの拡張機能をデバッグする場合は、レジストリの値を変更すると、拡張機能のトラブルシューティングに役立ちます。 この値は、HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools キーの下にあります。 既定では、これらの値は存在しません。  
  
 SharePoint ツールの拡張機能をトラブルシューティングする場合は、EnableDiagnostics 値を作成して設定できます。 その値を次の表に示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|EnableDiagnostics|診断メッセージが表示されるかどうかを指定する REG_DWORD、**出力**ウィンドウです。<br /><br /> 診断メッセージを表示する場合は、この値を 1 に設定します。 メッセージを表示しないようにするには、この値を 0 に設定するか、または削除します。<br /><br /> メッセージ ログを書き込む、**出力**ウィンドウ、SharePoint からツールの拡張機能を SharePoint プロジェクト サービスを使用します。 詳細については、次を参照してください。 [SharePoint プロジェクト サービスを使用して](../sharepoint/using-the-sharepoint-project-service.md)です。|  
  
 拡張機能に SharePoint コマンドが含まれる場合は、コマンドのトラブルシューティングに役立つ追加の値を作成して設定できます。 それらの値を次の表に示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|AttachDebuggerToHostProcess|vssphost4.exe の開始直後にデバッガーをアタッチできるダイアログ ボックスを表示するかどうかを指定する REG_DWORD です。 これは、デバッグするコマンドが vssphost.exe の開始直後にそのプロセスによって実行され、コマンドが実行される前に手動でデバッガーをアタッチする時間がない場合に役立ちます。 ダイアログ ボックスを表示するために、vssphost4.exe では、開始時に <xref:System.Diagnostics.Debugger.Break%2A> メソッドを呼び出します。<br /><br /> この動作を有効にするには、この値を 1 に設定します。 この動作を無効にするには、この値を 0 に設定するか、または削除します。<br /><br /> この値を 1 に設定すると、HostProcessStartupTimeout 値を増やすことが必要になる場合があります。これにより、vssphost4.exe が正常に開始されたことを Visual Studio に通知するまでの間に、ユーザーはデバッガーをアタッチできます。|  
|ChannelOperationTimeout|SharePoint コマンドの実行を待機する時間 (秒単位) を指定する REG_DWORD です。 時間内にコマンドが実行されない場合、<xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> がスローされます。<br /><br /> 既定値は 120 秒です。|  
|HostProcessStartupTimeout|vssphost4.exe が正常に開始されたことを vssphost4.exe が通知するのを待機する時間 (秒単位) を指定する REG_DWORD です。 時間内に vssphost4.exe から正常に開始されたことが通知されない場合、<xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> がスローされます。<br /><br /> 既定値は、60 秒です。|  
|MaxReceivedMessageSize|Visual Studio と vssphost4.exe の間で渡される WCF メッセージの最大許容サイズ (バイト単位) を指定する REG_DWORD です。<br /><br /> 既定値は 1,048,576 バイト (1 MB) です。|  
|MaxStringContentLength|Visual Studio と vssphost4.exe の間で渡される文字列の最大許容サイズ (バイト単位) を指定する REG_DWORD です。<br /><br /> 既定値は 1,048,576 バイト (1 MB) です。|  
  
## <a name="see-also"></a>参照  
 [Visual Studio での SharePoint ツールを拡張](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Visual Studio での SharePoint ツールの拡張機能の配置](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  