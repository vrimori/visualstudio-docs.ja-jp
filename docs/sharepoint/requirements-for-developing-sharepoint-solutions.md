---
title: "SharePoint ソリューションの開発要件 | Microsoft Docs"
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
  - "Visual Studio での SharePoint 開発, 必要条件"
  - "Visual Studio での SharePoint 開発, 要件"
ms.assetid: ae8ff69d-4540-4380-ab0b-845f7108e89c
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# SharePoint ソリューションの開発要件
  Visual Studio に付属の SharePoint ソリューション開発ツールを使用するには、あらかじめ次の必須コンポーネントをシステムにインストールしておく必要があります。  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)] または Visual Studio アプリケーション ライフサイクル管理 \(ALM\) のエディション  
  
    -   [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] をインストールする場合、[!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)] または [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] の機能のいずれか、または両方。  
  
-   64 ビット [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] または 64 ビット [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2 にインストールされた [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]。  
  
     または  
  
-   64 ビット [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] または 64 ビット [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] R2 にインストールされた [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]。  
  
> [!NOTE]  
>  SharePoint で正式にサポートされるのはサーバー オペレーティング システムだけですが、[!INCLUDE[win7](../sharepoint/includes/win7-md.md)] と [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1 の 2 つのクライアント オペレーティング システムは使用できます。  詳細については、「[Windows Vista、Windows 7、および Windows Server 2008 で SharePoint 2010 の開発環境をセットアップする](http://go.microsoft.com/fwlink/?LinkID=164557)」を参照してください。  
  
 Business Data Connectivity \(BDC\) モデル プロジェクト タイプの場合は、[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] がシステムにインストールされている必要があります。  
  
 SharePoint ソリューションを Visual Studio で開発するには、SharePoint を Visual Studio と同じコンピューターにインストールする必要があります。  また、SharePoint 開発者ツールは、SharePoint スタンドアロン構成のみをサポートします。ファーム \(リモート\) 構成はサポートしません。  
  
> [!NOTE]  
>  Visual Studio の SharePoint プロジェクトは、[!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)] のみサポートします。  新しい SharePoint プロジェクトに [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] を選択する場合、[!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)] も対象になります。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]をインストールする方法の詳細については、「[Visual Studio のインストール](../Topic/Installing%20Visual%20Studio.md)」を参照してください。  
  
## Vista と Windows 7 のユーザー アカウント制御 \(UAC\)  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] と [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] には、ユーザー アカウント制御 \(UAC: User Account Control\) と呼ばれるセキュリティ機能が組み込まれています。  [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] および [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] のシステム上の [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] で SharePoint ソリューションを開発する場合は、UAC により、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] をシステム管理者として実行することが求められます。  デスクトップで、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] のショートカット メニューを開き、**\[管理者として実行\]** をクリックします。  
  
 常に管理者として実行するようにデスクトップのショートカットを構成するには、ショートカット メニューを開いて **\[プロパティ\]** をクリックし、**\[詳細設定\]** をクリックして、**\[管理者として実行\]** チェック ボックスをオンにします。  
  
 詳細については、「[Windows Vista でのユーザー アカウント制御の理解と構成](http://go.microsoft.com/fwlink/?LinkID=156476)」および「[ユーザー アカウント制御](http://go.microsoft.com/fwlink/?LinkId=177523)」を参照してください。  
  
## SharePoint の権限に関する考慮事項  
 SharePoint ソリューションを開発するには、SharePoint ソリューションを実行し、デバッグするために十分な権限が必要です。  SharePoint ソリューションをテストする前に、次の手順に従って必要な権限を取得してください。  
  
1.  自分のユーザー アカウントをシステムの管理者として追加します。  
  
2.  自分のユーザー アカウントを SharePoint サーバーのファーム管理者として追加します。  
  
    1.  SharePoint サーバーの全体管理で、**\[ファーム管理者グループの管理\]** リンクをクリックします。  
  
    2.  **\[ファーム管理者\]** ページで、**\[新規作成\]** をクリックします。  
  
3.  自分のユーザー アカウントを WSS\_ADMIN\_WPG グループに追加します。  
  
## 参照  
 [Getting Started &#40;SharePoint Development in Visual Studio&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)  
  
  