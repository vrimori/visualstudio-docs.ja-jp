---
title: "SharePoint ソリューションのセキュリティ |Microsoft ドキュメント"
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
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
ms.assetid: 5ab33141-ba82-4960-8b29-3c907127fea6
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c57626827be8487d19cd546bc31bd32b0859cec7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="security-for-sharepoint-solutions"></a>SharePoint ソリューションのセキュリティ
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint アプリケーションのセキュリティを強化するために、次の機能が組み込まれています。  
  
## <a name="safe-control-entries"></a>安全なコントロール エントリ  
 作成されたすべての SharePoint プロジェクト項目[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]が、**安全なコントロール エントリ**を安全な場所を表すプロパティは、コレクションを制御します。 その**セーフ**サブプロパティでは、セキュリティで保護されたと見なされるコントロールを指定することができます。 詳細については、次を参照してください。[を提供するパッケージとプロジェクト項目での展開情報](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)と[セーフである Web パーツを指定する](http://go.microsoft.com/fwlink/?LinkId=177521)です。  
  
## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers 属性  
 既定では、ランタイム コード アクセス セキュリティ (CAS) システムによって完全に信頼されている唯一のアプリケーションは、共有マネージ コード アセンブリにアクセスできます。 AllowPartiallyTrustedCallers 属性を持つ完全に信頼されたアセンブリをマークすることにより、部分的に信頼されたアセンブリにアクセスできます。  
  
 AllowPartiallyTrustedCallers 属性がシステムのグローバル アセンブリ キャッシュに展開されていない SharePoint ソリューションに追加 ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)])。 これには、サンド ボックス ソリューションまたは SharePoint アプリケーションの Bin ディレクトリに配置されるソリューションが含まれます。 詳細については、次を参照してください。 [Microsoft .NET Framework のバージョン 1 のセキュリティ変更](http://go.microsoft.com/fwlink/?LinkId=177515)と[SharePoint Foundation の Web パーツを配置する](http://go.microsoft.com/fwlink/?LinkId=177509)です。  
  
## <a name="safe-against-script-property"></a>[スクリプト] プロパティに対して安全  
 *スクリプト インジェクション*は、コントロールや Web ページに悪意のあるコードを挿入します。 スクリプト インジェクションを SharePoint 2010 サイトを保護するため、共同作成者が表示または、既定の Web パーツまたはそれらのプロパティを編集できません。 この動作は、SafeAgainstScript という SafeControl 属性によって制御されます。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、プロジェクト項目にこの属性を設定**安全なコントロール エントリ**サブプロパティ**スクリプトに対して安全**です。 詳細については、次を参照してください。[を提供するパッケージとプロジェクト項目での展開情報](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)と[する方法: 安全なコントロールとしてマーク コントロール](../sharepoint/how-to-mark-controls-as-safe-controls.md)です。  
  
## <a name="vista-and-windows-7-user-account-control"></a>Vista および Windows 7 のユーザー アカウント制御  
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)]および[!INCLUDE[win7](../sharepoint/includes/win7-md.md)]ユーザー アカウント制御 (UAC) と呼ばれるセキュリティ機能を組み込みます。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] および [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] のシステム上の [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] で SharePoint ソリューションを開発する場合は、UAC により、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] をシステム管理者として実行することが求められます。 **開始**メニュー、ショートカット メニューを開き、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を選択し**管理者として実行**です。  
  
 構成する、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を常に管理者として実行、そのショートカット メニューを開き、選択ショートカット**プロパティ**、選択、 **[詳細設定]**ボタンをクリックして、**プロパティ**クリックしてダイアログ ボックスで、**管理者として実行**チェック ボックスをオンします。  
  
 詳細については、次を参照してください。 [Windows Vista のユーザー アカウント制御を構成すると理解](http://go.microsoft.com/fwlink/?LinkID=156476)です。 および[7 の Windows ユーザー アカウント制御](http://go.microsoft.com/fwlink/?LinkId=177523)です。  
  
## <a name="sharepoint-permissions-considerations"></a>SharePoint の権限に関する考慮事項  
 SharePoint ソリューションを開発するには、SharePoint ソリューションを実行し、デバッグするために十分な権限が必要です。 SharePoint ソリューションをテストする前に、次の手順に従って必要な権限を取得してください。  
  
1.  自分のユーザー アカウントをシステムの管理者として追加します。  
  
2.  自分のユーザー アカウントを SharePoint サーバーのファーム管理者として追加します。  
  
    1.  SharePoint 2010 サーバーの全体管理で、選択、**ファーム管理者グループの管理**リンクします。  
  
    2.  **ファーム管理者**ページで、選択、**新規**メニュー オプション  
  
3.  自分のユーザー アカウントを WSS_ADMIN_WPG グループに追加します。  
  
## <a name="additional-security-resources"></a>追加のセキュリティ リソース  
 セキュリティの問題に関する詳細については、次を参照してください。  
  
### <a name="visual-studio-security"></a>Visual Studio のセキュリティ  
  
-   [セキュリティとユーザーのアクセス許可](http://go.microsoft.com/fwlink/?LinkId=177503)  
  
-   [ネイティブ モードと .NET Framework コードでのセキュリティ](http://go.microsoft.com/fwlink/?LinkId=177504)  
  
-   [.NET Framework のセキュリティ](http://go.microsoft.com/fwlink/?LinkId=177502)  
  
### <a name="sharepoint-security"></a>SharePoint セキュリティ  
  
-   [SharePoint Foundation の管理とセキュリティ](http://go.microsoft.com/fwlink/?LinkId=177501)  
  
-   [SharePoint セキュリティ リソース センター](http://go.microsoft.com/fwlink/?LinkId=177498)  
  
-   [SharePoint Foundation の Web パーツをセキュリティで保護します。](http://go.microsoft.com/fwlink/?LinkId=177511)  
  
-   [Web アプリケーション セキュリティの向上: に関する脅威と対策](http://go.microsoft.com/fwlink/?LinkID=140080)  
  
### <a name="general-security"></a>一般的なセキュリティ  
  
-   [MSDN セキュリティ開発ライフ サイクル](http://go.microsoft.com/fwlink/?LinkID=147149)  
  
-   [セキュリティで保護された ASP.NET アプリケーションの構築: 認証、承認、およびセキュリティで保護された通信](http://go.microsoft.com/fwlink/?LinkId=177494)  
  
## <a name="see-also"></a>関連項目  
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)   
 [SharePoint ソリューションの開発要件](../sharepoint/requirements-for-developing-sharepoint-solutions.md)  
  
  