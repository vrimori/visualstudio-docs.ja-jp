---
title: "方法: WCF ワークフロー サービス アプリケーションを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: "14"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 62eeab72ab88094f7986bb29bd6f3a55ad6aeff6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>WCF ワークフロー サービス アプリケーションを作成する方法
[!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] ワークフロー サービス アプリケーションは、そのクライアントとの間でプロセスの境界を越えてメッセージを受け渡しする分散型の通信サービスです。 サービス側でのサービス コントラクトの実装は、.NET Framework 3.5 の従来のワークフロー サービスと同様に、[!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] のワークフロー アクティビティを介して宣言形式で行います。  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>WCF ワークフロー サービス アプリケーションを作成するには  
  
1.  [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] を起動します。  
  
2.  **ファイル**] メニューのをポイント**新規**、し、[**プロジェクト.**.  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  **インストールされたテンプレート**ペインで、 **WCF**または**ワークフロー**いずれかから、 **Visual c#**または**Visual Basic**任意の言語に応じてグループ化します。  
  
4.  中央のペインで選択**WCF ワークフロー サービス アプリケーション**です。  
  
5.  **名前**を識別しやすくようにプロジェクトのわかりやすい名前を入力します。  
  
6.  **場所**ボックスで、プロジェクトを保存ディレクトリを入力**参照**まで移動します。  
  
7.  **ソリューション**ボックスで、新しいソリューションを作成し、をクリックし、いずれかを選択**OK**です。  
  
    > [!NOTE]
    >  ワークフロー コンソール アプリケーションを既存のソリューションに追加する場合でそのソリューションを開きます[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]で、ソリューションを右クリックして**ソリューション エクスプ ローラー**を選択して**追加**、し**新しいプロジェクト.**を開くには、**新しいプロジェクト** ダイアログ ボックス。 上記の手順を実行します。  
  
8.  プロジェクト テンプレートによって、サービス定義が XAML として作成されます。 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]のデザイン ビューが開かれ、<xref:System.Activities.Statements.Sequence> と <xref:System.ServiceModel.Activities.Receive> のアクティビティを含む <xref:System.ServiceModel.Activities.SendReply> アクティビティが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [方法: アクティビティを作成します。](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)   
 [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)