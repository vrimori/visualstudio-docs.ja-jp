---
title: "方法: PolicyActivity ルール セット (レガシ) を作成 |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 96fcb8dd8e1255863840cae8edd90759af605f1d
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>方法: PolicyActivity ルール セットを作成する (レガシ)

このトピックを対象とする従来の Windows ワークフロー デザイナーを使用して設定ポリシー アクティビティのルールを作成する方法について説明、[!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)]または[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]です。

 ドラッグした後、**ポリシー**アクティビティ項目から、**ツールボックス**ワークフロー デザイン サーフェイスには、既存のルールを選択するか、新しいルールのセットを作成しますが、 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)アクティビティ。 既存のルールを使用して設定を選択する、[選択ルールを設定 ダイアログ ボックス (レガシ)](../workflow-designer/select-rule-set-dialog-box-legacy.md)を使用してルール セットを作成して、[ルール セット エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)です。

> [!NOTE]
> 開くことができます、[ルール セット エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)  ダイアログ ボックスをダブルクリックして直接、 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)ワークフロー デザイン サーフェイス上にあるアクティビティ。

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>PolicyActivity アクティビティ用のルール セットを選択または作成するには

1.  右クリックし、 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)、クリックして**プロパティ**を開くには、**プロパティ**ウィンドウです。

2.  クリックして、 **RuleSetReference**プロパティです。

3.  次のいずれかの操作を行います。

    -   クリックして、 **RuleSetReference**省略記号**[...]**、既存の規則セットを選択し、[選択ルールを設定 ダイアログ ボックス (レガシ)](../workflow-designer/select-rule-set-dialog-box-legacy.md)です。 次に、手順 10. に進みます。

         または

    -   ルール セットの名前を入力します。 クリックして、 **RuleSetReference**省略記号**[...]**、し、[**編集**で、[選択ルールを設定] ダイアログ ボックス (レガシ)](../workflow-designer/select-rule-set-dialog-box-legacy.md)です。

         - または -

    -   ルール セットの名前を入力します。 展開して、 **RuleSetReference**プロパティと、省略記号ボタンを選択**[...]**で、 **RuleSet 定義**プロパティです。

         [ルール セット エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)が開きます。

4.  [ルール セット エディター ダイアログ ボックス (レガシ)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)をクリックして**ルールの追加**ルール セットに新しいルールを追加します。

5.  入力してください、**名前**、**優先度**、および**再評価**プロパティ、または既定値を保持します。

6.  テキストを入力、**条件**です。

7.  テキストを入力、 **Then アクション**と**Else アクション**です。

8.  をクリックして**ルールの追加**別のルールを追加します。

9. 操作が完了したら、 **[OK]**をクリックします。

## <a name="see-also"></a>関連項目

- [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)
- [[ルール セットの選択] ダイアログ ボックス (レガシ)](../workflow-designer/select-rule-set-dialog-box-legacy.md)
- [[ルール セット エディター] ダイアログ ボックス (レガシ)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)
- [ポリシー アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)
- [従来のワークフロー アクティビティ](../workflow-designer/legacy-workflow-activities.md)