---
title: SharePoint ソリューションを開発するための要件 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, prerequisites
- SharePoint development in Visual Studio, requirements
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9c9d6a726b290bfed1c086f9fb03290a37c91490
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119399"
---
# <a name="requirements-for-developing-sharepoint-solutions"></a>SharePoint ソリューションの開発要件
Visual Studio に付属の SharePoint ソリューション開発ツールを使用するには、あらかじめ次の必須コンポーネントをシステムにインストールしておく必要があります。

- C# や Visual Basic、またはエディションの Visual Studio アプリケーション ライフ サイクル管理 (ALM) と visual Studio。

- [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 64 ビットにインストールされている[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]または 64 ビット[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]R2。

     または

- [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 64 ビットにインストールされている[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]または 64 ビット[!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]R2。

> [!NOTE]
> SharePoint で正式にサポートされるのはサーバー オペレーティング システムだけですが、[!INCLUDE[win7](../sharepoint/includes/win7-md.md)] と [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] SP1 の 2 つのクライアント オペレーティング システムは使用できます。 詳細については、次を参照してください。 [SharePoint Server 2010 開発者ワークステーションのインストール ガイド](http://go.microsoft.com/fwlink/?LinkID=164557)します。

Business Data Connectivity (BDC) モデル プロジェクト タイプの場合は、[!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] がシステムにインストールされている必要があります。

SharePoint ソリューションを Visual Studio で開発するには、SharePoint を Visual Studio と同じコンピューターにインストールする必要があります。 また、SharePoint 開発者ツールは、SharePoint スタンドアロン構成のみをサポートします。ファーム (リモート) 構成はサポートしません。

> [!NOTE]
> Visual Studio の SharePoint プロジェクトは、[!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)] のみサポートします。 新しい SharePoint プロジェクトに [!INCLUDE[net_v40_long](../sharepoint/includes/net-v40-long-md.md)] を選択する場合、[!INCLUDE[net_v35_long](../sharepoint/includes/net-v35-long-md.md)] も対象になります。

インストールする方法の詳細についての[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を参照してください[Visual Studio のインストール](../install/install-visual-studio.md)します。

## <a name="vista-and-windows-7-user-account-control-uac"></a>Vista と Windows 7 のユーザー アカウント制御 (UAC)
[!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] [!INCLUDE[win7](../sharepoint/includes/win7-md.md)]ユーザー アカウント制御 (UAC) と呼ばれるセキュリティ機能を組み込むことです。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] および [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] のシステム上の [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] で SharePoint ソリューションを開発する場合は、UAC により、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] をシステム管理者として実行することが求められます。 デスクトップで、ショートカット メニューを開き、[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]を選び、**管理者として実行**します。

常に管理者として実行するデスクトップ ショートカットを構成するには、ショートカット メニューを開き、**プロパティ**、選択、**詳細**ボタンをクリックし、選択、**管理者として実行**チェック ボックスをオンします。

詳細については、次を参照してください。 [Windows Vista のユーザー アカウント制御を構成すると理解](http://go.microsoft.com/fwlink/?LinkID=156476)します。 [Windows 7 ユーザー アカウント制御](http://go.microsoft.com/fwlink/?LinkId=177523)します。

## <a name="sharepoint-permissions-considerations"></a>SharePoint の権限に関する考慮事項
SharePoint ソリューションを開発するには、SharePoint ソリューションを実行し、デバッグするために十分な権限が必要です。 SharePoint ソリューションをテストする前に、次の手順に従って必要な権限を取得してください。

1. 自分のユーザー アカウントをシステムの管理者として追加します。

2. 自分のユーザー アカウントを SharePoint サーバーのファーム管理者として追加します。

    1. SharePoint サーバーの全体管理で、選択、**ファーム管理者グループの管理**リンク。

    2. **ファーム管理者**ページで、選択、**新規**ボタンをクリックします。

3. 自分のユーザー アカウントを WSS_ADMIN_WPG グループに追加します。

## <a name="see-also"></a>関連項目
[開始&#40;Visual Studio での SharePoint 開発&#41;](../sharepoint/getting-started-sharepoint-development-in-visual-studio.md)
