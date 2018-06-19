---
title: ワークフロー デザイナーの [ルール条件エディター] ダイアログ ボックス (レガシ)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2f723894f175cbf031c3a2ac61ed9eaec8e1c94f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975948"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>[ルール条件エディター] ダイアログ ボックス (レガシ)

このトピックについて説明する方法を使用して、**ルール条件エディター**従来の Windows ワークフロー デザイナー ダイアログ ボックス。 .NET Framework version 3.5、または、WinFX を対象とする必要がある場合は、従来のワークフロー デザイナーを使用します。

作成および使用して、宣言的ルール条件を変更する、**ルール条件エディター**  ダイアログ ボックス。 これらのルール条件は、Windows Workflow Foundation の事前定義アクティビティにプロパティとして公開されています。

-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)

-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)

-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)

-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)

-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)

-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)

アクセスする、**ルール条件エディター**  ダイアログ ボックスを使用して、[選択条件 ダイアログ ボックス (レガシ)](../workflow-designer/select-condition-dialog-box-legacy.md)です。

次の表は、ユーザー インターフェイス (UI) 要素の**ルール条件エディター**  ダイアログ ボックス。

|UI 要素|説明|
|----------------|-----------------|
|**条件:**|ルールの条件式を入力します。|
|**わかりました**|これをクリックすると、ルール条件が保存されます。|

## <a name="entering-condition-expressions"></a>条件式の入力

条件式は、テキストとして入力します。 入力**これです。** フィールド、プロパティ、およびワークフローで使用される方法を参照するエディターに IntelliSense のようなメニューを使用します。 または、ワークフローのメンバ名を直接入力することもできます。 条件には、AND、OR、NOT といった論理演算子を追加することもできます。 述語も追加できます。 述語は、バイナリ演算子と 2 つのオペランドから成ります。 サポートされているバイナリ演算子は**==**、 **>**、 **\<**、 **>=**、および **<=** です。 サポートされているオペランドは、定数値、算術関数、スコープ付きパブリック メンバです。

、比較の種類を指定してを比較できます**null**または空の文字列。 複合型を含む変数でメンバに対する呼び出しをネストすることができます (たとえば `this.Address.State == "WA"`)。

ルール条件エディタは、次の演算子をサポートします。

-   関係演算子 : ==、=、!=

-   比較演算子: <、 \<=、>、> =

-   算術演算子: +、-、 \*、/、MOD

-   論理演算子:、& &、OR、 &#124; &#124;、NOT、!

-   ビットごとの演算子: &、&#124;

式演算子の優先順位は、C# 演算子の優先順位規則に従います。

ルール条件エディタは、次の数式をサポートします。

this.i == 1D (1.0 に解決)

this.i == 1E1 (10.0 に解決)

this.i == 1L (long として解決)

this.i == 1M (decimal として解決)

this.i == 1F (single として解決)

this.i == 1U (unsigned int として解決)

条件の詳細については、次を参照してください。[ワークフローでの条件の使用](http://go.microsoft.com/fwlink?LinkID=65009)です。

## <a name="see-also"></a>関連項目

- [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)
- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)
- [[条件の選択] ダイアログ ボックス (レガシ)](../workflow-designer/select-condition-dialog-box-legacy.md)
- [ワークフローでの条件の使用](http://go.microsoft.com/fwlink?LinkID=65009)
- [従来の Designer for Windows Workflow Foundation UI ヘルプ](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)