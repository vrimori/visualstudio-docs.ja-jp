---
title: "制御フロー アクティビティ デザイナー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: ba74af23-5398-4e62-bd90-c50612e3bfef
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 7453a61f599b8d3e051fea1c016d914814ec7fd0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="control-flow-activity-designers"></a>制御フロー アクティビティ デザイナー
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]には、システムによって提供されるさまざまなアクティビティが用意されており、これらを、ワークフローの構築時に使用できます。 このセクションでは、ワークフロー内のフローの制御を目的とした、システムによって提供されるアクティビティを紹介します。 次のトピックでは、これらのアクティビティについて説明し、その使用方法についてのガイドラインを示します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)  
 本文に含まれる、少なくとも 1 回に、指定した条件が評価されるまで、アクティビティ実行**true**です。  
  
 [ForEach\<T >](http://msdn.microsoft.com/en-us/a680cddd-2760-497a-b27b-c023fcbc6f33)  
 指定したコレクション内の各項目に対して、本文に含まれるアクティビティを実行します。  
  
 [If](../workflow-designer/if-activity-designer.md)  
 条件を評価し、その評価の結果に応じてアクティビティを実行します。  
  
 [並列](../workflow-designer/parallel-activity-designer.md)  
 一連の子アクティビティを同時に実行します。  
  
 [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)  
 コレクションの要素を列挙し、コレクションの各要素に対して埋め込みステートメントを並列実行します。  
  
 [選択](../workflow-designer/pick-activity-designer.md)  
 イベント ベースのフロー制御を提供するイベントに応答して、複数の分岐の 1 つを実行します。  
  
 [PickBranch](../workflow-designer/pickbranch-activity-designer.md)  
 <xref:System.Activities.Statements.Pick> アクティビティ内で実行パスを提供します。  
  
 [シーケンス](../workflow-designer/sequence-activity-designer.md)  
 順番に実行される、子アクティビティの順序付きコレクションが含まれます。  
  
 [スイッチ\<T >](http://msdn.microsoft.com/en-us/ce1aa634-c4db-4475-a1c8-a88478a57212)  
 指定した式を評価し、その評価から得られた値と一致する関連付けられたキーを持つアクティビティのコレクションから、特定のアクティビティを実行します。  
  
 [While](../workflow-designer/while-activity-designer.md)  
 指定した条件が評価される場合に、本文に含まれているアクティビティ実行**true**です。  
  
## <a name="reference"></a>参照  
 <xref:System.Activities.Activity>  
  
 <xref:System.Activities.Statements.DoWhile>  
  
 <xref:System.Activities.Statements.ForEach%601>  
  
 <xref:System.Activities.Statements.If>  
  
 <xref:System.Activities.Statements.Parallel>  
  
 <xref:System.Activities.Statements.ParallelForEach%601>  
  
 <xref:System.Activities.Statements.Pick>  
  
 <xref:System.Activities.Statements.PickBranch>  
  
 <xref:System.Activities.Statements.Sequence>  
  
 <xref:System.Activities.Statements.Switch%601>  
  
 <xref:System.Activities.Statements.While>  
  
## <a name="related-sections"></a>関連項目  
 他の種類のアクティビティ デザイナーについては、次のトピックを参照してください。  
  
 [アクティビティ デザイナーの使用](../workflow-designer/using-the-activity-designers.md)  
  
 [フローチャート](../workflow-designer/flowchart-activity-designers.md)  
  
 [メッセージング](../workflow-designer/messaging-activity-designers.md)  
  
 [ランタイム](../workflow-designer/runtime-activity-designers.md)  
  
 [Primitives](../workflow-designer/primitives-activity-designers.md)  
  
 [トランザクション](../workflow-designer/transaction-activity-designers.md)  
  
 [コレクション](../workflow-designer/collection-activity-designers.md)  
  
 [エラー処理](../workflow-designer/error-handling-activity-designers.md)  
  
## <a name="external-resources"></a>外部リソース  
 [アクティビティ デザイナーの使用](../workflow-designer/using-the-activity-designers.md)