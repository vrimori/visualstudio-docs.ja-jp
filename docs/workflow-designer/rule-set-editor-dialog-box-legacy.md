---
title: "[ルール セット エディター] ダイアログ ボックス (レガシ) |Microsoft ドキュメント"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 989e0ed3f390513efeb849a71f94d5d61aecc57e
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2018
---
# <a name="rule-set-editor-dialog-box-legacy"></a>[ルール セット エディター] ダイアログ ボックス (レガシ)
このトピックについて説明する方法を使用して、**ルール セット エディター**従来の Windows ワークフロー デザイナー ダイアログ ボックス。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]を使用します。

 **ルール セット エディター**  ダイアログ ボックスを使用して作成および変更を[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)ルール セットで、.rules ファイルにシリアル化されます。

> [!NOTE]
> 使って .rules ファイルを開きたい場合、**エンコード付き XML エディタ**、ワークフローまたはアクティビティに関連付けられたデザイナー ウィンドウをまず閉じる必要があります。

 アクセスする方法については、**ルール セット エディター**ダイアログ ボックスを参照してください[する方法: PolicyActivity ルール セット (レガシ) を作成する](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)です。

> [!WARNING]
> [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] または [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] を対象とする場合に使用される、従来の[!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)]のルール エディターは、複数バージョン対応機能をサポートしていません。

 次の表は、ユーザー インターフェイス (UI) 要素の**ルール セット エディター**  ダイアログ ボックス。

|UI 要素|説明|
|----------------|-----------------|
|**規則を追加します。**|新しいルール定義をルール セットに追加します。|
|**削除**|選択したルールをルール セットから削除します。|
|**チェーン**|ルール セットで使用するフォワード チェーンの種類を指定します。 使用可能なオプションは次のとおりです。<br /><br /> -   **完全なチェーン**、すべてのフォワード チェーン メカニズムを使用するように指定する: 暗黙、メソッドの帰属、明示的なを使用して、**更新**関数。<br />-   **シーケンシャル**、フォワード チェーンをまったく使用しないことを指定します。<br />-   **明示的な更新プログラムのみ**、に対するフォワード チェーンだけを実行することを指定する**更新**アクション。<br /><br /> フォワード チェーンの詳細については、次を参照してください。 [PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)です。|
|**Name**|ルール セット リストの列見出しです。 ルール リストを名前で並べ替えるには、これをクリックします。|
|**優先順位**|ルール セット リストの列見出しです。 ルール リストを優先度で並べ替えるには、これをクリックします。|
|**再評価**|ルール セット リストの列見出しです。 ルール リストを再評価タイプで並べ替えるには、これをクリックします。|
|**ルールのプレビュー**|ルール セット リストの列見出しです。 ルールの条件とアクションのプレビューでルール リストを並べ替えるには、これをクリックします。|
|**[名前]:**|ルールの名前を入力します。|
|**優先順位:**|ルールの優先度を入力します。 既定の優先順位は 0 です。|
|**再評価します。**|ルールで使用するルール再評価の種類を指定します。 使用可能なオプションは次のとおりです。<br /><br /> -   **常に**、それが原因で、ルールが必要に応じてに再評価されます。<br />-   **決して**、それが原因で、規則を再評価することはありません。 この場合、ルールは一度だけ実行されます。|
|**アクティブ**|これをオンにすると、ルールはアクティブになります。|
|**条件:**|ルールの条件式を入力します。 式の構文の詳細については、このページの「条件式とアクション式の入力」の項を参照してください。|
|**Then アクション:**|Then アクションの式を入力します。 式の構文の詳細については、このページの「条件式とアクション式の入力」の項を参照してください。|
|**Else アクション:**|Else アクションの式を入力します。 式の構文の詳細については、このページの「条件式とアクション式の入力」の項を参照してください。|
|**OK**|これをクリックすると、ルール セットが .rules ファイルに保存されます。|

 ルール セットの詳細については、次を参照してください。 [PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)です。

## <a name="entering-condition-and-action-expressions"></a>条件式とアクション式の入力
 条件で、[次の式を入力すると、それ以外の場合、該当するテキスト文字列としてのアクションのボックス、**ルール セット エディター** ] ダイアログ ボックス。 入力**これです。** フィールド、プロパティ、およびワークフローで使用される方法を参照するエディターにメニューの IntelliSense の種類を使用します。 または、ワークフローのメンバ名を直接入力することもできます。 クラス名とそれに続いてメソッド名を入力することにより、参照された型で静的メソッドを呼び出すことができます。

 条件には、AND、OR、NOT といった論理演算子を追加することもできます。 述語も追加できます。 述語は、バイナリ演算子と 2 つのオペランドから成ります。 サポートされているバイナリ演算子は = =、>、 \<、> =、および < = です。 サポートされているオペランドは、定数値、算術関数、スコープ付きパブリック メンバです。

 、比較の種類を指定してを比較できます**null**または空の文字列。 複合型を含む変数でメンバに対する呼び出しをネストすることができます (たとえば `this.Address.State == "WA"`)。

 式では、次の演算子がサポートされます。

-   関係演算子 : ==、=、!=

-   比較演算子: <、 \<=、>、> =

-   算術演算子 : +、-、*、/、MOD

-   論理演算子:、& &、OR、 &#124; &#124;、NOT、!

-   ビットごとの演算子: &、&#124;

 式演算子の優先順位は、C# 演算子の優先順位規則に従います。

 条件の詳細については、次を参照してください。[ワークフローでの条件の使用](http://msdn.microsoft.com/en-us/541211f5-d382-4810-894f-71f00b34fa77)です。

### <a name="halt-and-update-functions"></a>Halt 関数と Update 関数
 **Then アクション:**と**Else アクション:**式は、サポート**停止**と**更新**関数。 使用する、**停止**関数、入力**停止**に、**し、アクション:**または**Else アクション:**テキスト ボックス。 **停止**操作によって、ルール セットの実行をすぐに停止して、呼び出し元のコードに制御が戻ります。 使用する、**更新**フォワード チェーンを持つ関数です。

 **更新**ステートメントは、エディターの 2 つの形式で表すことができます。 両方の形式は次の例で表示されます。

```
Update(this.Address.State)
Update("this/Address/State")
```

 使用しての詳細については**更新**フォワード チェーンで次を参照してください。 [PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)です。

## <a name="see-also"></a>関連項目

- [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)
- [[ルール セットの選択] ダイアログ ボックス (レガシ)](../workflow-designer/select-rule-set-dialog-box-legacy.md)
- [PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)
- [ワークフローでの条件の使用](http://go.microsoft.com/fwlink?LinkID=65009)