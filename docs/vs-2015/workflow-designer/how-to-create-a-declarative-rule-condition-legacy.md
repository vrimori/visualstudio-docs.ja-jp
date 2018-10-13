---
title: '方法: 宣言的ルール条件 (レガシ) の作成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 2508404840db81f03ba4865a3e5d5af91e5c653b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49187413"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>方法: 宣言的ルール条件を作成する (レガシ)
このトピックでは、[!INCLUDE[wfd1](../includes/wfd1-md.md)] または [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] を対象とする従来の [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]を使用してルール条件を宣言する方法について説明します。  
  
 条件ステートメントの評価が**True**または**False**します。 宣言的ルール条件は、条件ステートメントを使用して作成される、[ルール条件エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)ワークフローを XML として格納されているとします。 複数の述語を結合したブール値演算とワークフロー ステートとを比較する述語を含めることができます。  
  
 宣言的ルール条件は、次のような Windows Workflow Foundation 事前定義アクティビティで使用されます。  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>ルール条件エディタを使って宣言的ルール条件を作成するには  
  
1.  アクティビティの**プロパティ**ウィンドウで、をクリックして、**条件**プロパティまたは**UntilCondition**アクティビティに応じてプロパティ。  
  
2.  選択**宣言型ルール条件**プロパティの一覧から。  
  
3.  展開、**条件**または**UntilCondition**プロパティ。  
  
4.  をクリックして、 **ConditionName**プロパティ。  
  
5.  をクリックして、 **ConditionName**楕円 **[...]** を開く、**条件の選択** ダイアログ ボックス。  
  
6.  クリックして**新しい条件**を開く、**ルール条件エディター**  ダイアログ ボックス。  
  
7.  条件の式を入力、**条件**テキスト ボックス。  
  
     条件式を作成する方法については、次を参照してください。[ルール条件エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)します。  
  
8.  条件式の作成が完了したら、クリックして**OK**ダイアログ ボックスを閉じ、割り当て済みの名前を持つルールの条件を作成します。  
  
     **条件の選択** ダイアログ ボックスが表示されます。  
  
     使用する方法については、**条件の選択**ダイアログ ボックスを参照してください[選択条件 ダイアログ ボックス (レガシ)](../workflow-designer/select-condition-dialog-box-legacy.md)します。  
  
## <a name="see-also"></a>関連項目  
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)   
 [Conditionedactivitygroup アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65066)   
 [IfElseBranchActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Replicator アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65080)   
 [While を使用してアクティビティ](http://go.microsoft.com/fwlink?LinkID=65091)   
 [ルール条件エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [条件の選択 ダイアログ ボックス (レガシ)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [ワークフロー内での条件の使用](http://go.microsoft.com/fwlink?LinkID=65009)