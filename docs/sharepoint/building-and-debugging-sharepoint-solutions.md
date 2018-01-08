---
title: "ビルドと SharePoint ソリューションのデバッグ |Microsoft ドキュメント"
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
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
ms.assetid: c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 47ff77e26ede1c8f9c1bf35b8fc3e69a7951d24c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="building-and-debugging-sharepoint-solutions"></a>SharePoint ソリューションのビルドとデバッグ
  一般に、ビルドと SharePoint ソリューションのデバッグは、ビルドおよびその他の種類のプロジェクトのデバッグと同じ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 このセクションのトピックでは、いくつかある相違点について説明します。  
  
## <a name="project-output-for-sharepoint-solutions"></a>SharePoint ソリューションのプロジェクトの出力  
 SharePoint ソリューションの構築は、アセンブリおよびソリューション パッケージ (.wsp) ファイルを作成します。 次の表は、ビルド時にこれらのファイルの場所を示します。  
  
|ビルド項目|出力フォルダー|  
|----------------|-------------------|  
|アセンブリ、プログラム データベース (PDB) および .wsp ファイル。|*ProjectName*\bin\debug または*ProjectName*\bin\release|  
|SharePoint プロジェクト項目ファイル。|*ProjectName*\pkg\debug または*ProjectName*\pkg\release|  
|中間ファイルをビルドします。|*ProjectName*\obj\debug または*ProjectName*\obj\release|  
|パッケージの中間ファイル。|*ProjectName*\pkgobj\debug または*ProjectName*\pkgobj\release|  
  
## <a name="building-sharepoint-solutions"></a>SharePoint ソリューションの構築  
 SharePoint ソリューションをビルドするには、インストールされた SharePoint サーバーの正しいバージョンが、開発用コンピューターに必要です。 それ以外の場合、SharePoint ソリューションの構築は、その他の種類のプロジェクトをビルドする場合と同じ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 詳細については、次を参照してください。[する方法: SharePoint ソリューションのビルド](../sharepoint/how-to-build-sharepoint-solutions.md)です。  
  
## <a name="debugging-and-testing-sharepoint-solutions"></a>デバッグと、SharePoint ソリューションのテスト  
 デバッグする前に[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint サーバーに .wsp パッケージをコピー、サイトと Web スコープの機能をアクティブにし、場合によっては、プロジェクトを開始します。 それ以外の場合は、プロジェクトを手動で開く必要があります。 詳細については、次を参照してください。 [SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)と[SharePoint ソリューションのデバッグ](../sharepoint/debugging-sharepoint-solutions.md)です。  
  
## <a name="debugging-and-verifying-sharepoint-solutions-by-using-alm-features"></a>デバッグおよび ALM 機能を使用した SharePoint ソリューションの検証  
 単体テストと IntelliTrace などの visual Studio ALM 機能には、SharePoint ソリューションの正確に特定の問題の詳細に有効にします。 プロファイルを使用すると、検索し、SharePoint ソリューションのパフォーマンス問題の領域を識別できます。 詳細については、次を参照してください。 [SharePoint コードのデバッグの検証と](../sharepoint/verifying-and-debugging-sharepoint-code.md)と[SharePoint アプリケーションのパフォーマンスのプロファイリング](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)です。  
  
## <a name="security-during-the-build-process"></a>ビルド プロセス中のセキュリティ  
 パッケージまたは SharePoint ソリューションを配置する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint サーバーにファイルをコピーするアクセス許可が必要です。 実行する必要があります[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]昇格されたプロセスと、ユーザー アカウントが SharePoint サーバー上のサイト コレクション管理者をする必要があります。 さらに、プロジェクトはサンド ボックス ソリューションまたはファーム ソリューションかどうかを指定する必要があります。 詳細については、次を参照してください。[違いサンド ボックス ソリューションとファーム ソリューション](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)です。  
  
## <a name="using-the-clean-command"></a>［クリーン］ コマンドの使用  
 SharePoint ソリューションのデバッグは、SharePoint サーバーのインストール時に、**クリーン**コマンドでは、ソリューションはアンインストールされません。 代わりに、SharePoint 構成から機能を非アクティブ化する必要があります。  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)   
 [サーバー エクスプ ローラーを使用して SharePoint 接続の参照](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  