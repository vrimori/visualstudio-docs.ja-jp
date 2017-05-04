---
title: "Debugging Extensions for the SharePoint Tools in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, debugging extensions"
ms.assetid: 7cee8ce0-d07b-41f6-8ce1-b18e4be3b50c
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Debugging Extensions for the SharePoint Tools in Visual Studio
  Visual Studio の実験用インスタンスまたは通常のインスタンスで、SharePoint ツールの拡張機能をデバッグできます。  拡張機能の動作をトラブルシューティングする必要がある場合は、レジストリ値を変更して、追加のエラー情報を表示し、Visual Studio での SharePoint コマンドの実行方法を構成することもできます。  
  
## Visual Studio の実験用インスタンスで拡張機能をデバッグする  
 テストされていない拡張機能による不慮の破損から Visual Studio 開発環境を保護するために、Visual Studio SDK には、拡張機能のインストールおよびテストに使用できる代替の Visual Studio インスタンス \(*実験用インスタンス*と呼ばれます\) が用意されています。  新しい拡張機能は Visual Studio の通常のインスタンスを使用して開発しますが、デバッグと実行は実験用インスタンスで行います。  詳細については、「[実験用インスタンス](../extensibility/the-experimental-instance.md)」を参照してください。  
  
 VSIX プロジェクトを使用して拡張機能を配置し、その VSIX プロジェクトをソリューションのスタートアップ プロジェクトにする場合は、ソリューションをデバッグするときに、実験用インスタンスで拡張機能が自動的にインストールされて実行されます。  スタートアップ プロジェクトとは、複数のプロジェクトを含むソリューションをデバッグするときに開始されるプロジェクトです。  VSIX プロジェクトを使用して拡張機能を配置する方法の詳細については、「[Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)」を参照してください。  スタートアップ プロジェクトの詳細については、「[方法 : スタートアップ プロジェクトを設定する](http://msdn.microsoft.com/ja-jp/31465836-0911-48db-a5d9-e456b635e970)」を参照してください。  
  
 Visual Studio の実験用インスタンスでさまざまな種類の拡張機能をデバッグする方法を示す例については、次のチュートリアルを参照してください。  
  
-   [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## Visual Studio の通常のインスタンスで拡張機能をデバッグする  
 Visual Studio の通常のインスタンスで拡張機能プロジェクトをデバッグするには、まず、その拡張機能を通常のインスタンスにインストールします。  次に、デバッガーを Visual Studio の第 2 プロセスにアタッチします。  デバッグの完了後、拡張機能を削除して、開発用コンピューターに読み込まれないようにすることができます。  
  
#### 拡張機能をインストールするには  
  
1.  Visual Studio のすべてのインスタンスを閉じます。  
  
2.  拡張機能プロジェクトのビルド出力フォルダーで、.vsix ファイルをダブルクリックして開くか、そのファイルのショートカット メニューを開いて **\[開く\]** をクリックします。  
  
3.  **\[Visual Studio 拡張機能インストーラー\]** ダイアログ ボックスで、拡張機能のインストール先となる Visual Studio のエディションを選択し、**\[インストール\]** をクリックします。  
  
     拡張機能のファイルが %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions\\*author name*\\*extension name*\\*version* にインストールされます。  このパスの最後の 3 つのフォルダーは、拡張機能の extension.vsixmanifest ファイル内の `Author`、`Name`、および `Version` の各要素から構築されます。  
  
4.  拡張機能がインストールされたら、**\[閉じる\]** をクリックします。  
  
#### 拡張機能をデバッグするには  
  
1.  管理者特権で Visual Studio を起動し、拡張機能プロジェクトを開きます。  以下の手順では、Visual Studio のこのインスタンスを*第 1 インスタンス*と呼びます。  
  
2.  Visual Studio の別のインスタンスを管理者特権で起動します。  以下の手順では、Visual Studio のこのインスタンスを*第 2 インスタンス*と呼びます。  
  
3.  Visual Studio の第 1 インスタンスに切り替えます。  
  
4.  メニュー バーで **\[デバッグ\]**、**\[プロセスにアタッチ\]** の順にクリックします。  
  
5.  **\[選択可能なプロセス\]** ボックスの一覧で \[devenv.exe\] を選択します。  これが、Visual Studio の第 2 インスタンスを表します。プロジェクトの拡張機能は、このインスタンスでデバッグすることになります。  
  
6.  **\[アタッチ\]** をクリックします。  
  
     Visual Studio によって拡張機能プロジェクトがデバッグ モードで実行されます。  
  
7.  Visual Studio の第 2 インスタンスに切り替えます。  
  
8.  拡張機能を読み込む新しい SharePoint プロジェクトを作成します。  たとえば、リスト定義プロジェクト項目の拡張機能をデバッグする場合は、**\[リスト定義\]** プロジェクトを作成します。  
  
9. 拡張機能のコードのテストに必要な手順をすべて実行します。  
  
10. 拡張機能のデバッグが完了したら、Visual Studio の第 2 インスタンスを閉じます。  
  
#### 拡張機能を削除するには  
  
1.  Visual Studio のメニュー バーで **\[ツール\]**、**\[拡張機能と更新プログラム\]** の順にクリックします。  
  
     **\[拡張機能と更新プログラム\]** ダイアログ ボックスが表示されます。  
  
2.  拡張機能の一覧で拡張機能の名前を選択し、**\[アンインストール\]** をクリックします。  
  
3.  確認のダイアログ ボックスが表示されたら、**\[はい\]** をクリックして、拡張機能をアンインストールします。  
  
4.  **\[今すぐ再起動\]** をクリックするとアンインストールは完了です。  
  
## SharePoint コマンドのデバッグ  
 SharePoint ツールの拡張機能に属している SharePoint コマンドをデバッグする場合は、vssphost4.exe プロセスにデバッガーをアタッチする必要があります。  これは、SharePoint コマンドを実行する 64 ビット ホスト プロセスです。  SharePoint コマンドと vssphost4.exe の詳細については、「[Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md)」を参照してください。  
  
#### vssphost4.exe プロセスにデバッガーをアタッチするには  
  
1.  前に説明した手順に従って、Visual Studio の実験用インスタンスまたは Visual Studio の通常のインスタンスで拡張機能のデバッグを開始します。  
  
2.  デバッガーを実行する Visual Studio のインスタンスのメニュー バーで **\[デバッグ\]**、**\[プロセスにアタッチ\]** の順にクリックします。  
  
3.  **\[選択可能なプロセス\]** ボックスの一覧で \[vssphost.exe\] を選択します。  
  
    > [!NOTE]  
    >  vssphost.exe が一覧に表示されない場合は、拡張機能を実行する Visual Studio のインスタンスで vssphost4.exe プロセスを開始する必要があります。  通常、そのためには、Visual Studio によって開発コンピューター上の SharePoint サイトに接続する操作を実行します。  たとえば、**サーバー エクスプローラー** ウィンドウの **\[SharePoint 接続\]** ノードの下にあるサイト接続ノード \(サイトの URL を表示するノード\) を展開する場合、または特定の SharePoint プロジェクト項目 \(**リスト インスタンス**項目や**イベント レシーバー**項目など\) を SharePoint プロジェクトに追加する場合に、Visual Studio では vssphost4.exe を開始します。  
  
4.  **\[アタッチ\]** をクリックします。  
  
5.  デバッグ対象の Visual Studio のインスタンスで、コマンドの実行に必要な手順を実行します。  
  
## SharePoint ツールの拡張機能のデバッグが簡単になるようにレジストリ値を変更する  
 Visual Studio の SharePoint ツールの拡張機能をデバッグする場合は、レジストリの値を変更すると、拡張機能のトラブルシューティングに役立ちます。  この値は、HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools キーの下にあります。  既定では、これらの値は存在しません。  
  
 SharePoint ツールの拡張機能をトラブルシューティングする場合は、EnableDiagnostics 値を作成して設定できます。  その値を次の表に示します。  
  
|値|説明|  
|-------|--------|  
|EnableDiagnostics|診断メッセージを **\[出力\]** ウィンドウに表示するかどうかを指定する REG\_DWORD です。<br /><br /> 診断メッセージを表示する場合は、この値を 1 に設定します。  メッセージを表示しないようにするには、この値を 0 に設定するか、または削除します。<br /><br /> SharePoint ツールの拡張機能からメッセージを **\[出力\]** ウィンドウに書き込むには、SharePoint プロジェクト サービスを使用します。  詳細については、「[Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md)」を参照してください。|  
  
 拡張機能に SharePoint コマンドが含まれる場合は、コマンドのトラブルシューティングに役立つ追加の値を作成して設定できます。  それらの値を次の表に示します。  
  
|値|説明|  
|-------|--------|  
|AttachDebuggerToHostProcess|vssphost4.exe の開始直後にデバッガーをアタッチできるダイアログ ボックスを表示するかどうかを指定する REG\_DWORD です。  これは、デバッグするコマンドが vssphost.exe の開始直後にそのプロセスによって実行され、コマンドが実行される前に手動でデバッガーをアタッチする時間がない場合に役立ちます。  ダイアログ ボックスを表示するために、vssphost4.exe では、開始時に <xref:System.Diagnostics.Debugger.Break%2A> メソッドを呼び出します。<br /><br /> この動作を有効にするには、この値を 1 に設定します。  この動作を無効にするには、この値を 0 に設定するか、または削除します。<br /><br /> この値を 1 に設定すると、HostProcessStartupTimeout 値を増やすことが必要になる場合があります。これにより、vssphost4.exe が正常に開始されたことを Visual Studio に通知するまでの間に、ユーザーはデバッガーをアタッチできます。|  
|ChannelOperationTimeout|SharePoint コマンドの実行を待機する時間 \(秒単位\) を指定する REG\_DWORD です。  時間内にコマンドが実行されない場合、<xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> がスローされます。<br /><br /> 既定値は 120 秒です。|  
|HostProcessStartupTimeout|vssphost4.exe が正常に開始されたことを vssphost4.exe が通知するのを待機する時間 \(秒単位\) を指定する REG\_DWORD です。  時間内に vssphost4.exe から正常に開始されたことが通知されない場合、<xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> がスローされます。<br /><br /> 既定値は 60 秒です。|  
|MaxReceivedMessageSize|Visual Studio と vssphost4.exe の間で渡される WCF メッセージの最大許容サイズ \(バイト単位\) を指定する REG\_DWORD です。<br /><br /> 既定値は 1,048,576 バイト \(1 MB\) です。|  
|MaxStringContentLength|Visual Studio と vssphost4.exe の間で渡される文字列の最大許容サイズ \(バイト単位\) を指定する REG\_DWORD です。<br /><br /> 既定値は 1,048,576 バイト \(1 MB\) です。|  
  
## 参照  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  