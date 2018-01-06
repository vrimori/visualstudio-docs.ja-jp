---
title: "サンド ボックス間の相違点とファーム ソリューション |Microsoft ドキュメント"
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
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6c13d27f8c79f1bc638741d8877ac95a0dff4885
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>サンドボックス ソリューションとファーム ソリューションの違い
  SharePoint ソリューションをコンパイルするときに、SharePoint サーバーに展開しをデバッグするデバッガーをアタッチします。 ソリューションのデバッグに使用するプロセスは、サンド ボックス ソリューション プロパティの設定によって異なります。: サンド ボックス ソリューションまたはファーム ソリューションです。  
  
 詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)です。  
  
## <a name="farm-solutions"></a>ファーム ソリューション  
 IIS ワーカー プロセス (W3WP.exe) でホストされる、ファーム ソリューションでは、ファーム全体に影響を与えるコードを実行します。 サンド ボックス ソリューション プロパティが設定される「ファーム ソリューション」を SharePoint プロジェクトをデバッグするときに SharePoint の取り消しまたは IIS ワーカー プロセスによってロックされているすべてのファイルが解放されるように機能を展開する前に、システムの IIS アプリケーション プールがリサイクルされます。 SharePoint プロジェクトのサイトの URL を提供している IIS アプリケーション プールのみがリサイクルされます。  
  
## <a name="sandboxed-solutions"></a>サンド ボックス ソリューション  
 サンド ボックス ソリューションは、SharePoint ユーザーのコード ソリューション ワーカー プロセス (SPUCWorkerProcess.exe) でホストするは、ソリューションのサイト コレクションにのみ影響を与えるコードを実行します。 サンド ボックス ソリューションは、IIS ワーカー プロセスでは実行されない、ため、IIS アプリケーション プールでも、IIS サーバーを再起動する必要があります。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]SharePoint で SPUserCodeV4 サービスが自動的にトリガーする SPUCWorkerProcess プロセスとコントロールにデバッガーをアタッチします。 SPUCWorkerProcess プロセスがソリューションの最新バージョンの読み込みをリサイクルする必要はありません。  
  
## <a name="either-type-of-solution"></a>ソリューションのいずれかの種類  
 どちらのソリューションの種類と[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]も、ブラウザー クライアント側スクリプトのデバッグを有効にするデバッガーをアタッチします。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]スクリプトのデバッグをこの目的のエンジンを使用します。 スクリプトのデバッグを有効にするには、入力を求められたら、既定のブラウザー設定を変更する必要があります。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]現在のサイトを実行している W3WP または SPUCWorkerProcess プロセスにのみ、デバッガーをアタッチします。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]また、マネージ COM + とワークフローのデバッグ エンジンをアタッチします。  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションのデバッグ](../sharepoint/debugging-sharepoint-solutions.md)   
 [SharePoint ソリューションのビルドとデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [サンドボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)  
  
  