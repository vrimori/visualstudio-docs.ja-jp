---
title: "方法: アクティビティ ライブラリを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
caps.latest.revision: "12"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a61c8f4ea5e9d9cc6d4ab13437d2ec4d4eef7ca
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-an-activity-library"></a>アクティビティ ライブラリを作成する方法
カスタム アクティビティは、ワークフローで特定のビジネス プロセスをモデル化するために使用されます。 [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] のアクティビティ ライブラリ テンプレートでは、[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]を使用して、こうしたカスタム アクティビティを視覚的に作成できます。  
  
### <a name="to-create-a-workflow-activity-library"></a>ワークフロー アクティビティ ライブラリを作成するには  
  
1.  [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] を起動します。  
  
2.  **ファイル**] メニューのをポイント**新規**、し、[**プロジェクト.**.  
  
     **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
3.  **プロジェクトの種類**ペインで、**ワークフロー**いずれかから、 **Visual c#**プロジェクトまたは**Visual Basic**に応じてグループ化、言語の優先順位。  
  
4.  **テンプレート**ペインで、**アクティビティ ライブラリ**です。  
  
5.  **名前** ボックスを識別しやすく、プロジェクトのわかりやすい名前を入力します。  
  
6.  **場所**ボックスで、プロジェクトを保存ディレクトリ タイプで**参照**まで移動します。  
  
7.  **ソリューション**ボックスに、ソリューションのわかりやすい名前を入力し、をクリックして**OK**です。  
  
    > [!NOTE]
    >  ワークフロー コンソール アプリケーションを既存のソリューションに追加する場合でそのソリューションを開きます[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]で、ソリューションを右クリックして**ソリューション エクスプ ローラー**を選択して**追加**、し**新しいプロジェクト.**を開くには、**新しいプロジェクト** ダイアログ ボックス。 上記の手順を実行します。  
  
8.  プロジェクト テンプレートによって、XAML でアクティビティ定義が作成されます。 [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] で、カスタム アクティビティ用のキャンバスが開かれて表示されます。  
  
9. アクティビティをドラッグして、**ツールボックス**に、カスタム アクティビティに含めるデザイン画面にします。  
  
    > [!CAUTION]
    >  カスタム アクティビティの本体に含めることができる子アクティビティは 1 つのみです。ただし、その子アクティビティは、<xref:System.Activities.Statements.Sequence> アクティビティや <xref:System.Activities.Statements.Flowchart> アクティビティなどの複合アクティビティにすることができます。  
  
## <a name="see-also"></a>関連項目  
 [方法: アクティビティを作成します。](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)   
 [ワークフロー プロジェクトの作成](../workflow-designer/creating-a-workflow-project.md)