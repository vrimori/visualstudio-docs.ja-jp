---
title: サンド ボックスの相違点とファーム ソリューション |Microsoft Docs
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
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 282fe23a9a586d79b745efec99bc014e88777fd6
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326333"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>サンド ボックスの相違点とファーム ソリューション
  SharePoint ソリューションをコンパイルするときに、SharePoint サーバーにデプロイされ、それをデバッグするデバッガーをアタッチします。 ソリューションのデバッグに使用されるプロセスは、サンド ボックス ソリューション プロパティの設定によって異なります。 サンド ボックス ソリューションまたはファーム ソリューション。  
  
 詳細については、次を参照してください。[サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)します。  
  
## <a name="farm-solutions"></a>ファーム ソリューション
 IIS ワーカー プロセス (W3WP.exe) でホストされているファーム ソリューションでは、ファーム全体に影響を与えるコードを実行します。 「ファーム ソリューション」をサンド ボックス ソリューション プロパティが設定されている SharePoint プロジェクトをデバッグするときに、SharePoint または IIS ワーカー プロセスによってロックされているすべてのファイルをリリースするための機能をデプロイする前に、システムの IIS アプリケーション プールがリサイクルされます。 SharePoint プロジェクトのサイトの URL を提供している IIS アプリケーション プールのみは、リサイクルされます。  
  
## <a name="sandboxed-solutions"></a>サンド ボックス ソリューション
 SharePoint ユーザーのコード ソリューション ワーカー プロセス (SPUCWorkerProcess.exe) でホストされている、サンド ボックス ソリューションは、ソリューションのサイト コレクションにのみ影響を与えるコードを実行します。 サンド ボックス ソリューションは、IIS ワーカー プロセスでは実行できない、ため、IIS アプリケーション プールでも、IIS サーバーを再起動する必要があります。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint で SPUserCodeV4 サービスが自動的にトリガーする SPUCWorkerProcess プロセスとコントロールには、デバッガーをアタッチします。 ソリューションの最新バージョンの読み込みをリサイクルする SPUCWorkerProcess プロセスの必要はありません。  
  
## <a name="either-type-of-solution"></a>ソリューションのいずれかの種類
 いずれのソリューション タイプ[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]もクライアント側スクリプトのデバッグを有効にするブラウザーにデバッガーがアタッチされます。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] デバッグ エンジンはこの目的のためのスクリプトを使用します。 スクリプトのデバッグを有効にするには、求められたら、既定のブラウザー設定を変更する必要があります。  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 現在のサイトを実行している W3WP または SPUCWorkerProcess プロセスにのみ、デバッガーをアタッチします。 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] また、マネージ COM + とワークフローのデバッグ エンジンをアタッチします。  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションをデバッグします。](../sharepoint/debugging-sharepoint-solutions.md)   
 [ビルドし、SharePoint ソリューションのデバッグ](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [サンド ボックス ソリューションの考慮事項](../sharepoint/sandboxed-solution-considerations.md)  
  
