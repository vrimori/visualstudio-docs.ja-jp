---
title: "SharePoint ソリューションのセキュリティ"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "セキュリティ [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, セキュリティ"
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# SharePoint ソリューションのセキュリティ
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] には、SharePoint アプリケーションのセキュリティ強化に役立つ次のような機能が組み込まれています。  
  
## 安全なコントロール エントリ  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で作成されたすべての SharePoint プロジェクト項目には、**\[安全なコントロール エントリ\]** というプロパティがあります。このプロパティは、安全なコントロールのコレクションを表します。  このプロパティの **\[安全\]** サブプロパティを使用すると、安全と見なされるコントロールを指定できます。  詳細については、[プロジェクト項目でのパッケージ化と配置の情報の提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) を参照します [安全な Web パーツの指定](http://go.microsoft.com/fwlink/?LinkId=177521)。  
  
## AllowPartiallyTrustedCallers 属性  
 既定では、ランタイム コード アクセス セキュリティ \(CAS: code access security\) システムによって完全に信頼されたアプリケーションのみが共有マネージ コード アセンブリにアクセスできますが、  完全に信頼されたアセンブリを AllowPartiallyTrustedCallers 属性でマークすると、部分的に信頼されたアセンブリからそのアセンブリにアクセスできるようになります。  
  
 AllowPartiallyTrustedCallers 属性は、システムのグローバル アセンブリ キャッシュ \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]: global assembly cache\) に配置されない SharePoint ソリューション   \(サンドボックス ソリューション、SharePoint アプリケーションの Bin ディレクトリに配置されるソリューションなど\) に追加されます。  詳細については、[Microsoft.NET Framework のバージョン 1 Security Changes](http://go.microsoft.com/fwlink/?LinkId=177515) 参照します [SharePoint Foundation の Deploying Web Parts](http://go.microsoft.com/fwlink/?LinkId=177509)。  
  
## \[スクリプトに対して安全\] プロパティ  
 悪質な可能性があるコードをコントロールや Web ページに挿入されることを、*スクリプト インジェクション*と呼びます。  既定では、SharePoint 2010 サイトをスクリプト インジェクションから保護するために、共同作成者は Web パーツやそのプロパティを表示したり編集したりできないようになっています。  この動作は、SafeAgainstScript という SafeControl 属性によって制御されます。  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] でこの属性を設定するには、プロジェクト項目の **\[安全なコントロール エントリ\]** プロパティの **\[スクリプトに対して安全\]** サブプロパティを使用します。  詳細については、「[プロジェクト項目でのパッケージ化と配置の情報の提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)」および「[方法: コントロールを安全なコントロールとしてマークする](../sharepoint/how-to-mark-controls-as-safe-controls.md)」を参照してください。  
  
## Vista と Windows 7 のユーザー アカウント制御  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] と [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] には、ユーザー アカウント制御 \(UAC: User Account Control\) と呼ばれるセキュリティ機能が組み込まれています。  [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] および [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] のシステム上の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で SharePoint ソリューションを開発する場合は、UAC により、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] をシステム管理者として実行することが求められます。  **\[開始\]** メニューから、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]のショートカット メニューを開き、**\[管理者として実行\]** をクリックします。  
  
 管理者は、ショートカット メニューを開き、**\[プロパティ\]** をクリックします、**\[プロパティ\]** ダイアログ ボックスの **\[詳細\]** ボタンを選択し、選択するように [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] を常に実行するタスクを通るように設定するには **\[管理者として実行\]** のチェック ボックスをオンにします。  
  
 詳細については、「[Windows Vista でのユーザー アカウント制御の理解と構成](http://go.microsoft.com/fwlink/?LinkID=156476)」および「[ユーザー アカウント制御](http://go.microsoft.com/fwlink/?LinkId=177523)」を参照してください。  
  
## SharePoint の権限に関する考慮事項  
 SharePoint ソリューションを開発するには、SharePoint ソリューションを実行し、デバッグするために十分な権限が必要です。  SharePoint ソリューションをテストする前に、次の手順に従って必要な権限を取得してください。  
  
1.  自分のユーザー アカウントをシステムの管理者として追加します。  
  
2.  自分のユーザー アカウントを SharePoint サーバーのファーム管理者として追加します。  
  
    1.  SharePoint 2010 のサーバーの全体管理で、**\[ファーム管理者グループの管理\]** リンクをクリックします。  
  
    2.  **\[ファームの管理者\]** ページで、**\[新規作成\]** メニュー オプションを選択します。  
  
3.  自分のユーザー アカウントを WSS\_ADMIN\_WPG グループに追加します。  
  
## その他のセキュリティ リソース  
 セキュリティの問題の詳細については、次のトピックを参照してください。  
  
### Visual Studio のセキュリティ  
  
-   [セキュリティとユーザー アクセス許可](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [ネイティブ コードと .NET Framework のセキュリティ](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [.NET Framework のセキュリティ](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### SharePoint のセキュリティ  
  
-   [SharePoint Foundation Administration とセキュリティ](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [SharePoint のセキュリティ リソース センター](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [SharePoint Foundation の Securing Web Parts](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Web Application Security の強化: 脅威や対策](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### セキュリティ全般  
  
-   [MSDN のセキュリティ開発ライフサイクル](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [ビルドの安全な ASP.NET Applications: 認証、承認、セキュリティで保護された通信](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## 参照  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  