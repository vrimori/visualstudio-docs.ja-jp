---
title: ルール セット エディター ダイアログ ボックス (レガシ) |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 2b7c7965d7f9af42dc25a91c750a6ec633fedc73
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538528"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>[ルール セット エディター] ダイアログ ボックス (レガシ)
このトピックで説明する方法を使用して、**ルール セット エディター**  ダイアログ ボックスで、従来の[!INCLUDE[wfd1](../includes/wfd1-md.md)]します。 [!INCLUDE[wfd2](../includes/wfd2-md.md)] または [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] を対象とする必要がある場合は、従来の[!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]を使用します。  
  
 **ルール セット エディター**ダイアログ ボックスを使用して作成および変更を[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)ルール セットは .rules ファイルにシリアル化します。  
  
> [!NOTE]
>  使って .rules ファイルを開きたい場合、**エンコード付き XML エディター**、ワークフローまたはアクティビティに関連付けられているデザイナー ウィンドウをまず閉じる必要があります。  
  
 アクセスする方法については、**ルール セット エディター**ダイアログ ボックスを参照してください[方法: PolicyActivity ルール セット (レガシ) を作成する](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)します。  
  
> [!WARNING]
>  [!INCLUDE[wfd2](../includes/wfd2-md.md)] または [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] を対象とする場合に使用される、従来の[!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]のルール エディターは、複数バージョン対応機能をサポートしていません。  
  
 次の表に、ユーザー インターフェイス (UI) 要素の**ルール セット エディター**  ダイアログ ボックス。  
  
|UI 要素|説明|  
|----------------|-----------------|  
|**ルールを追加します。**|新しいルール定義をルール セットに追加します。|  
|**削除**|選択したルールをルール セットから削除します。|  
|**チェーン**|ルール セットで使用するフォワード チェーンの種類を指定します。 使用可能なオプションは次のとおりです。<br /><br /> -   **完全なチェーン**、すべてのフォワード チェーン メカニズムを使用することを指定する: 暗黙、メソッドの帰属、明示的な使用して、**更新**関数。<br />-   **シーケンシャル**、フォワード チェーンをまったく使用しないように指定します。<br />-   **明示的な更新プログラムのみ**、に対するフォワード チェーンだけを実行することを指定する**Update**アクション。<br /><br /> フォワード チェーンの詳細については、次を参照してください。 [PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)します。|  
|**Name**|ルール セット リストの列見出しです。 ルール リストを名前で並べ替えるには、これをクリックします。|  
|**優先順位**|ルール セット リストの列見出しです。 ルール リストを優先度で並べ替えるには、これをクリックします。|  
|**再評価**|ルール セット リストの列見出しです。 ルール リストを再評価タイプで並べ替えるには、これをクリックします。|  
|**ルールのプレビュー**|ルール セット リストの列見出しです。 ルールの条件とアクションのプレビューでルール リストを並べ替えるには、これをクリックします。|  
|**名:**|ルールの名前を入力します。|  
|**優先順位:**|ルールの優先度を入力します。 既定の優先順位は 0 です。|  
|**再評価します。**|ルールで使用するルール再評価の種類を指定します。 使用可能なオプションは次のとおりです。<br /><br /> -   **常に**、必要に応じて、再評価するルールします。<br />-   **決して**、それが原因で、ルールを再評価することはありません。 この場合、ルールは一度だけ実行されます。|  
|**アクティブ**|これをオンにすると、ルールはアクティブになります。|  
|**条件:**|ルールの条件式を入力します。 式の構文の詳細については、このページの「条件式とアクション式の入力」の項を参照してください。|  
|**Then アクション:**|Then アクションの式を入力します。 式の構文の詳細については、このページの「条件式とアクション式の入力」の項を参照してください。|  
|**Else アクション:**|Else アクションの式を入力します。 式の構文の詳細については、このページの「条件式とアクション式の入力」の項を参照してください。|  
|**わかりました**|これをクリックすると、ルール セットが .rules ファイルに保存されます。|  
  
 規則セットの詳細については、次を参照してください。 [PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)します。  
  
## <a name="entering-condition-and-action-expressions"></a>条件式とアクション式の入力  
 条件で、[次の式を入力すると、それ以外の場合、それぞれのテキストのテキストとしてアクションのボックス、**ルール セット エディター** ] ダイアログ ボックス。 入力**これです。** フィールド、プロパティ、およびワークフローで使用される方法を参照するエディターにメニューの IntelliSense 型を使用します。 または、ワークフローのメンバ名を直接入力することもできます。 クラス名とそれに続いてメソッド名を入力することにより、参照された型で静的メソッドを呼び出すことができます。  
  
 条件には、AND、OR、NOT といった論理演算子を追加することもできます。 述語も追加できます。 述語は、バイナリ演算子と 2 つのオペランドから成ります。 サポートされているバイナリ演算子は = =、>、 \<、> =、および < = です。 サポートされているオペランドは、定数値、算術関数、スコープ付きパブリック メンバです。  
  
 比較の種類を指定でき、比較できます**null**または空の文字列。 複合型を含む変数でメンバに対する呼び出しをネストすることができます (たとえば `this.Address.State == "WA"`)。  
  
 式では、次の演算子がサポートされます。  
  
-   関係演算子 : ==、=、!=  
  
-   比較演算子: <、 \<=、>、> =  
  
-   算術演算子 : +、-、*、/、MOD  
  
-   論理演算子:、& &、OR、 &#124; &#124;、NOT、!  
  
-   ビットごとの演算子: &、&#124;  
  
 式演算子の優先順位は、C# 演算子の優先順位規則に従います。  
  
 条件の詳細については、次を参照してください。[ワークフロー内の条件を使用して](http://msdn.microsoft.com/en-us/541211f5-d382-4810-894f-71f00b34fa77)します。  
  
### <a name="halt-and-update-functions"></a>Halt 関数と Update 関数  
 **Then アクション:** と**Else アクション:** 式をサポートする**Halt**と**Update**関数。 使用する、 **Halt**関数、入力**Halt**に、 **Then アクション:** または**Else アクション:** テキスト ボックス。 **Halt**操作によって、ルール セットの実行をすぐに停止して、呼び出し元のコードに制御が戻ります。 使用する、 **Update**フォワード チェーンを持つ関数です。  
  
 **Update**ステートメントは、エディターの 2 つの形式で表すことができます。 どちらの形式が次の例で示すようにします。  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 使用しての詳細については**Update**フォワード チェーンで次を参照してください。 [PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)します。  
  
## <a name="see-also"></a>関連項目  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [[ルール セット] ダイアログ ボックス (レガシ)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [PolicyActivity アクティビティの使用](http://go.microsoft.com/fwlink?LinkID=65004)   
 [ワークフロー内での条件の使用](http://go.microsoft.com/fwlink?LinkID=65009)