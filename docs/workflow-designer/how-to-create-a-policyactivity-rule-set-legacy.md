---
title: "方法: PolicyActivity ルール セットを作成する (レガシ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "PolicyActivity アクティビティ, ルール セットの作成"
  - "PolicyActivity アクティビティ, ルール セットの選択"
  - "[ルール セット エディター] ダイアログ ボックス"
  - "ルール セット, PolicyActivity 用に作成"
  - "[ルール セットの選択] ダイアログ ボックス"
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# 方法: PolicyActivity ルール セットを作成する (レガシ)
このトピックでは、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] または [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] を対象とする従来の [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]を使用してポリシー アクティビティのルール セットを作成する方法について説明します。  
  
 **\[ポリシー\]** アクティビティ項目を **\[ツールボックス\]** からワークフロー デザイン サーフェイスにドラッグした後、[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) アクティビティ用に既存のルールを選択するか、新しいルール セットを作成できます。既存のルール セットを選択するには [\[ルール セットの選択\] ダイアログ ボックス \(レガシ\)](../Topic/Select%20Rule%20Set%20Dialog%20Box%20\(Legacy\).md) を使用し、ルール セットを作成するには [\[ルール セット エディター\] ダイアログ ボックス \(レガシ\)](../Topic/Rule%20Set%20Editor%20Dialog%20Box%20\(Legacy\).md) を使用します。  
  
> [!NOTE]
>  [\[ルール セット エディター\] ダイアログ ボックス \(レガシ\)](../Topic/Rule%20Set%20Editor%20Dialog%20Box%20\(Legacy\).md)を直接開くには、ワークフロー デザイン サーフェイス上の [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) アクティビティをダブルクリックします。  
  
### PolicyActivity アクティビティ用のルール セットを選択または作成するには  
  
1.  [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) を右クリックし、**\[プロパティ\]** をクリックして **\[プロパティ\]** ウィンドウを開きます。  
  
2.  **\[RuleSetReference\]** プロパティをクリックします。  
  
3.  以下のいずれかを実行します。  
  
    -   **\[RuleSetReference\]** の **\[…\]** をクリックして、[\[ルール セットの選択\] ダイアログ ボックス \(レガシ\)](../Topic/Select%20Rule%20Set%20Dialog%20Box%20\(Legacy\).md)で既存のルール セットを選択します。次に、手順 10. に進みます。  
  
         または  
  
    -   ルール セットの名前を入力します。**\[RuleSetReference\]** の **\[...\]** をクリックして、[\[ルール セットの選択\] ダイアログ ボックス \(レガシ\)](../Topic/Select%20Rule%20Set%20Dialog%20Box%20\(Legacy\).md)で **\[編集\]** を選択します。  
  
         または  
  
    -   ルール セットの名前を入力します。**\[RuleSetReference\]** プロパティを展開して、**\[RuleSet 定義\]** プロパティの **\[...\]** をクリックします。  
  
         [\[ルール セット エディター\] ダイアログ ボックス \(レガシ\)](../Topic/Rule%20Set%20Editor%20Dialog%20Box%20\(Legacy\).md)が開きます。  
  
4.  [\[ルール セット エディター\] ダイアログ ボックス \(レガシ\)](../Topic/Rule%20Set%20Editor%20Dialog%20Box%20\(Legacy\).md)で、**\[ルールの追加\]** をクリックして新しいルールをルール セットに追加します。  
  
5.  **\[名前\]**、**\[優先度\]**、**\[再評価\]** の各プロパティに入力するか、既定値を使用します。  
  
6.  **\[条件\]** にテキストを入力します。  
  
7.  **\[THEN アクション\]** および **\[ELSE アクション\]** にテキストを入力します。  
  
8.  別のルールを追加するには、**\[ルールの追加\]** をもう一度クリックします。  
  
9. 作業が終了したら、**\[OK\]** をクリックします。  
  
## 参照  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [\[ルール セットの選択\] ダイアログ ボックス \(レガシ\)](../Topic/Select%20Rule%20Set%20Dialog%20Box%20\(Legacy\).md)   
 [\[ルール セット エディター\] ダイアログ ボックス \(レガシ\)](../Topic/Rule%20Set%20Editor%20Dialog%20Box%20\(Legacy\).md)   
 [ポリシー アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)   
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)