---
title: '方法: PolicyActivity ルール セットを作成 (レガシ) |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 7ab49957d830bf558a9dddf55cdc5e8c2f3f75d2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194624"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>方法: PolicyActivity ルール セットを作成する (レガシ)
このトピックでは、[!INCLUDE[wfd1](../includes/wfd1-md.md)] または [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] を対象とする従来の [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]を使用してポリシー アクティビティのルール セットを作成する方法について説明します。  
  
 ドラッグした後、**ポリシー**アクティビティ項目から、**ツールボックス**、ワークフロー デザイン サーフェイスには、既存のルールを選択するか、新しい規則のセットを作成しますが、 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)アクティビティ。 既存のルールを使用して設定を選択する、[選択ルールを設定 ダイアログ ボックス (レガシ)](../workflow-designer/select-rule-set-dialog-box-legacy.md)を使用してルール セットを作成して、[ルール セット エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)します。  
  
> [!NOTE]
>  開くことができます、[ルール セット エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)  ダイアログ ボックスをダブルクリックして、直接、 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)ワークフロー デザイン サーフェイス上にあるアクティビティ。  
  
### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>PolicyActivity アクティビティ用のルール セットを選択または作成するには  
  
1.  右クリックし、 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)、 をクリックし、**プロパティ**を開く、**プロパティ**ウィンドウ。  
  
2.  をクリックして、 **RuleSetReference**プロパティ。  
  
3.  次のいずれかの操作を行います。  
  
    -   をクリックして、 **RuleSetReference**楕円 **[...]**、既存の規則セットをクリックして、[選択ルールを設定 ダイアログ ボックス (レガシ)](../workflow-designer/select-rule-set-dialog-box-legacy.md)します。 次に、手順 10. に進みます。  
  
         または  
  
    -   ルール セットの名前を入力します。 をクリックして、 **RuleSetReference**楕円 **[...]**、し、[**編集**で、[選択ルールを設定] ダイアログ ボックス (レガシ)](../workflow-designer/select-rule-set-dialog-box-legacy.md)します。  
  
         - または -  
  
    -   ルール セットの名前を入力します。 展開、 **RuleSetReference**プロパティと、省略記号ボタンを選択します **[...]** で、 **RuleSet 定義**プロパティ。  
  
         [ルール セット エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)が開きます。  
  
4.  [ルール セット エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)、 をクリックして**規則の追加**規則セットに新しい規則を追加します。  
  
5.  入力、**名前**、**優先度**と**再評価**プロパティ、または既定値を保持します。  
  
6.  テキストを入力、**条件**します。  
  
7.  テキストを入力、 **Then アクション**と**Else アクション**します。  
  
8.  クリックして**規則の追加**別のルールを追加するには、もう一度です。  
  
9. 操作が完了したら、 **[OK]** をクリックします。  
  
## <a name="see-also"></a>関連項目  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [[ルール セット] ダイアログ ボックス (レガシ)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [ルール セット エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [ポリシー アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)   
 [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)