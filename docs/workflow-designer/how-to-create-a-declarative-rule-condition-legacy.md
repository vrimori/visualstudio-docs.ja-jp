---
title: "方法: 宣言的ルール条件を作成する (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "条件ステートメント, 宣言的ルール条件"
  - "宣言的ルール条件"
  - "[ルール条件エディター] ダイアログ ボックス"
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# 方法: 宣言的ルール条件を作成する (レガシ)
このトピックでは、[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]を使用してルール条件を宣言する方法について説明します。  
  
 条件ステートメントは、**True** または **False** として評価されます。宣言的ルール条件とは、[\[ルール条件エディター\] ダイアログ ボックス \(レガシ\)](../Topic/Rule%20Condition%20Editor%20Dialog%20Box%20\(Legacy\).md)を使って作成され、XML としてワークフローと共に保存される条件ステートメントです。複数の述語を結合したブール値演算とワークフロー ステートとを比較する述語を含めることができます。  
  
 宣言的ルール条件は、次のような Windows Workflow Foundation 事前定義アクティビティで使用されます。  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### ルール条件エディタを使って宣言的ルール条件を作成するには  
  
1.  アクティビティの **\[プロパティ\]** ウィンドウで、アクティビティに応じて **\[Condition\]** プロパティまたは **\[UntilCondition\]** プロパティをクリックします。  
  
2.  プロパティの一覧から **\[宣言型のルール条件\]** を選択します。  
  
3.  **\[Condition\]** または **\[UntilCondition\]** プロパティを展開します。  
  
4.  **\[ConditionName\]** プロパティをクリックします。  
  
5.  **\[ConditionName\]** の **\[...\]** をクリックすると、**\[条件の選択\]** ダイアログ ボックスが開きます。  
  
6.  **\[新しい条件\]** をクリックして **\[ルール条件エディター\]** ダイアログ ボックスを表示します。  
  
7.  条件式を **\[条件\]** ボックスに入力します。  
  
     条件式を作成する方法については、「[\[ルール条件エディター\] ダイアログ ボックス \(レガシ\)](../Topic/Rule%20Condition%20Editor%20Dialog%20Box%20\(Legacy\).md)」を参照してください。  
  
8.  条件式の作成が終わったら、**\[OK\]** をクリックすると、ダイアログ ボックスが閉じて指定した名前のルール条件が作成されます。  
  
     **\[条件の選択\]** ダイアログ ボックスが開きます。  
  
     **\[条件の選択\]** ダイアログ ボックスの使用方法については、「[\[条件の選択\] ダイアログ ボックス \(レガシ\)](../Topic/Select%20Condition%20Dialog%20Box%20\(Legacy\).md)」を参照してください。  
  
## 参照  
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)   
 [ConditionedActivityGroup の使用](http://go.microsoft.com/fwlink?LinkID=65066)   
 [IfElseBranchActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Replicator アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65080)   
 [While アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65091)   
 [\[ルール条件エディター\] ダイアログ ボックス \(レガシ\)](../Topic/Rule%20Condition%20Editor%20Dialog%20Box%20\(Legacy\).md)   
 [\[条件の選択\] ダイアログ ボックス \(レガシ\)](../Topic/Select%20Condition%20Dialog%20Box%20\(Legacy\).md)   
 [ワークフロー内での条件の使用](http://go.microsoft.com/fwlink?LinkID=65009)