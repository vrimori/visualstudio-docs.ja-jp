---
title: "方法: 宣言的ルール条件 (レガシ) を作成 |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 2cd288086ffce4474c86cc4e87178ea173ff2e43
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>方法: 宣言的ルール条件を作成する (レガシ)
このトピックを対象とする従来の Windows ワークフロー デザイナーを使用してルールの条件を宣言する方法について説明、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)]または[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]です。

 条件ステートメントの評価が**True**または**False**です。 宣言的ルール条件は、条件ステートメントを使用して作成される、[ルール条件エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)ワークフローに XML として格納されているとします。 複数の述語を結合したブール値演算とワークフロー ステートとを比較する述語を含めることができます。

 宣言的ルール条件は、次のような Windows Workflow Foundation 事前定義アクティビティで使用されます。

-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>ルール条件エディタを使って宣言的ルール条件を作成するには

1.  アクティビティの**プロパティ**ウィンドウで、をクリックして、**条件**プロパティまたは**UntilCondition**アクティビティに応じてプロパティです。

2.  選択**宣言的ルール条件**プロパティの一覧からです。

3.  展開して、**条件**または**UntilCondition**プロパティです。

4.  クリックして、 **ConditionName**プロパティです。

5.  クリックして、 **ConditionName**省略記号**[...]**を開くには、 **[条件の**] ダイアログ ボックス。

6.  をクリックして**新しい条件**を開くには、**ルール条件エディター**  ダイアログ ボックス。

7.  条件の式を入力、**条件**テキスト ボックス。

     条件式を作成する方法については、次を参照してください。[ルール条件エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)です。

8.  条件式の作成が完了したら、をクリックして**OK**  ダイアログ ボックスを閉じ、割り当てられた名前を持つルールの条件を作成します。

     **[条件の**] ダイアログ ボックスが表示されます。

     使用する方法については、 **[条件の**ダイアログ ボックスを参照してください[選択条件] ダイアログ ボックス (レガシ)](../workflow-designer/select-condition-dialog-box-legacy.md)です。

## <a name="see-also"></a>関連項目

- [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)
- [ConditionedActivityGroup を使用します。](http://go.microsoft.com/fwlink?LinkID=65066)
- [IfElseBranchActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65075)
- [レプリケーター アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65080)
- [While を使用してアクティビティ](http://go.microsoft.com/fwlink?LinkID=65091)
- [[ルール条件エディター] ダイアログ ボックス (レガシ)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)
- [[条件の選択] ダイアログ ボックス (レガシ)](../workflow-designer/select-condition-dialog-box-legacy.md)
- [ワークフローでの条件の使用](http://go.microsoft.com/fwlink?LinkID=65009)