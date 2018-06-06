---
title: ビルドと SharePoint ソリューションのデバッグ |Microsoft ドキュメント
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
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4d0bc3185b0684f96bf31cc127cd852448afe772
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34765071"
---
# <a name="build-and-debug-sharepoint-solutions"></a>ビルドおよび SharePoint ソリューションのデバッグ
  一般に、ビルドと SharePoint ソリューションのデバッグは、ビルドおよびその他の種類のプロジェクトのデバッグと同じ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 このセクションのトピックでは、いくつかある相違点について説明します。  
  
## <a name="project-output-for-sharepoint-solutions"></a>SharePoint ソリューションのプロジェクトの出力
 アセンブリおよびソリューション パッケージを作成する SharePoint ソリューションの構築 (*.wsp*) ファイル。 次の表は、ビルド時にこれらのファイルの場所を示します。  
  
|ビルド項目|出力フォルダー|  
|----------------|-------------------|  
|アセンブリ、プログラム データベース (*.pdb*)、および *.wsp*ファイル。|*{Projectname} \bin\debug*または *{projectname} \bin\release*|  
|SharePoint プロジェクト項目ファイル。|*{Projectname} \pkg\debug*または *{projectname} \pkg\release*|  
|中間ファイルをビルドします。|*{Projectname} \obj\debug*または *{projectname} \obj\release*|  
|パッケージの中間ファイル。|*{Projectname} \pkgobj\debug*または *{projectname} \pkgobj\release*|  
  
## <a name="build-sharepoint-solutions"></a>SharePoint ソリューションをビルドします。
 SharePoint ソリューションをビルドするには、インストールされた SharePoint サーバーの正しいバージョンが、開発用コンピューターに必要です。 それ以外の場合、SharePoint ソリューションの構築は、その他の種類のプロジェクトをビルドする場合と同じ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。 詳細については、次を参照してください。[する方法: SharePoint ソリューションのビルド](../sharepoint/how-to-build-sharepoint-solutions.md)です。  
  
## <a name="debug-and-test-sharepoint-solutions"></a>デバッグし、SharePoint ソリューションのテスト
 デバッグする前に[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]コピー、 *.wsp* SharePoint サーバーにパッケージが、サイトと Web スコープ機能をアクティブにし、場合によっては、プロジェクトを開始します。 それ以外の場合は、プロジェクトを手動で開く必要があります。 詳細については、次を参照してください。 [SharePoint ソリューションのトラブルシューティング](../sharepoint/troubleshooting-sharepoint-solutions.md)と[SharePoint ソリューションのデバッグ](../sharepoint/debugging-sharepoint-solutions.md)です。  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-alm-features"></a>デバッグおよび ALM 機能を使用して SharePoint ソリューションを確認してください。
 単体テストと IntelliTrace などの visual Studio ALM 機能には、SharePoint ソリューションの正確に特定の問題の詳細に有効にします。 プロファイルを使用すると、検索し、SharePoint ソリューションのパフォーマンス問題の領域を識別できます。 詳細については、次を参照してください。 [SharePoint コードのデバッグの検証と](../sharepoint/verifying-and-debugging-sharepoint-code.md)と[SharePoint アプリケーションのパフォーマンスのプロファイリング](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)です。  
  
## <a name="security-during-the-build-process"></a>ビルド プロセス中のセキュリティ
 パッケージまたは SharePoint ソリューションを配置する[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint サーバーにファイルをコピーするアクセス許可が必要です。 実行する必要があります[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]昇格されたプロセスと、ユーザー アカウントが SharePoint サーバー上のサイト コレクション管理者をする必要があります。 さらに、プロジェクトはサンド ボックス ソリューションまたはファーム ソリューションかどうかを指定する必要があります。 詳細については、次を参照してください。[違いサンド ボックス ソリューションとファーム ソリューション](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)です。  
  
## <a name="using-the-clean-command"></a>[クリーン] コマンドを使用します。  
 SharePoint ソリューションのデバッグは、SharePoint サーバーのインストール時に、**クリーン**コマンドでは、ソリューションはアンインストールされません。 代わりに、SharePoint 構成から機能を非アクティブ化する必要があります。  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションの開発](../sharepoint/developing-sharepoint-solutions.md)   
 [サーバー エクスプ ローラーを使用して SharePoint 接続の参照](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [SharePoint ソリューションのパッケージ化と配置](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
 