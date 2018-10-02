---
title: ParallelForEach&lt;T&gt;アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 7a384844ca8d41b9e40de13c7dc7bc161d6c09f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536085"
---
# <a name="parallelforeachlttgt-activity-designer"></a>ParallelForEach&lt;T&gt;アクティビティ デザイナー
<xref:System.Activities.Statements.ParallelForEach%601> アクティビティでは、コレクションの要素を列挙し、コレクションの各要素に対して埋め込みステートメントを並列的に (同じスレッドで非同期的に) 実行します。 このフロー制御アクティビティは、その子アクティビティがアイドル状態になると予想される場合に、<xref:System.Activities.Statements.Sequence> アクティビティの代わりに使用します。  
  
 <xref:System.Activities.Statements.ParallelForEach%601> アクティビティには、ユーザーによって指定された <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> 式を保持する [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] プロパティがあります。 このプロパティは、各分岐の完了後に、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティによって評価されます。 評価されると、 **true**、<xref:System.Activities.Statements.ParallelForEach%601>アクティビティが他の分岐を実行せずに完了します。 場合、<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>に評価されない**true**、<xref:System.Activities.Statements.ParallelForEach%601>アクティビティのすべての子アクティビティが完了したときに完了します。  
  
## <a name="the-parallelforeacht-activity"></a>ParallelForEach\<T > アクティビティ  
 <xref:System.Activities.Statements.ParallelForEach%601> はそれ自体の値を列挙し、列挙した値ごとに <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> をスケジュールします。 スケジュールされるのは <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> のみです。 本文の実行方法は、<xref:System.Activities.Statements.ParallelForEach%601.Body%2A> がアイドル状態になるかどうかによって異なります。  
  
 <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> がアイドル状態にならない場合は、スケジュールされたアクティビティがスタックとして扱われるため、逆の順序で実行されます。つまり、最後にスケジュールされたアクティビティが最初に実行されます。 コレクションがある場合など{1,2,3,4}で<xref:System.Activities.Statements.ParallelForEach%601>を使用して、 **WriteLine**値を書き込む本文として。この場合は、4、3、2、1 の順にコンソールに出力されます。 これは、ため**WriteLine** 4 の後にアイドル状態のためには説明しません**WriteLine**アクティビティがスケジュールされた、スタックの動作を使用してを実行する (最初の出し)。  
  
 ただし、<xref:System.Activities.Statements.ParallelForEach%601.Body%2A> アクティビティや <xref:System.ServiceModel.Activities.Receive> アクティビティのように、アイドル状態になる可能性のあるアクティビティが <xref:System.Activities.Statements.Delay> に含まれている場合は、 それぞれのアクティビティが完了するまで待機する必要はありません。 <xref:System.Activities.Statements.ParallelForEach%601> は、スケジュールされている次の本文アクティビティに進み、実行を試みます。 そのアクティビティもアイドル状態になる場合は、<xref:System.Activities.Statements.ParallelForEach%601> が、さらに次の本文アクティビティに進みます。  
  
### <a name="using-the-parallelforeacht-activity-designer"></a>ParallelForEach を使用して\<T > アクティビティ デザイナー  
 **ParallelForEach\<T >** アクティビティ デザイナーが記載されて、**制御フロー**のカテゴリ、**ツールボックス**をクリックしてアクセスします。**ツールボックス** タブの左側にある、 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X)。  
  
 **ParallelForEach\<T >** からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]アクティビティ デザイナーは、通常、任意の場所を画面のたとえば、内部の**シーケンス**アクティビティ デザイナー。 ドロップすると、[!INCLUDE[wfd2](../includes/wfd2-md.md)]が作成されます、<xref:System.Activities.Statements.ParallelForEach%601>を既定で含む、アクティビティ、<xref:System.Activities.Activity.DisplayName%2A>の**ParallelForEach\<Int32 > です。**  
  
### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach\<T > のワークフロー デザイナーでのプロパティ  
 次の表に、最も役に立つ <xref:System.Activities.Statements.ParallelForEach%601> アクティビティのプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーのアクティビティ デザイナーの表示名を指定します。 既定値は**ParallelForEach\<Int32 >** します。 値を必要に応じて編集、**プロパティ**グリッドまたは直接アクティビティ デザイナーのヘッダー。|  
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|コレクション内の各項目に対して実行するアクティビティ。 追加する、<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>アクティビティ、アクティビティをツールボックスからドロップ、**本文**ボックスに、 **ParallelForEach\<T >** アクティビティ デザイナーの「ドロップ アクティビティここ」ヒント テキスト。|  
|**TypeArgument**|True|内の項目の種類、<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>ジェネリック パラメーターで指定されたコレクション*T*します。既定では、 **TypeArgument**に設定されている**Int32**します。 型 T を変更する、 **ParallelForEach\<T >** アクティビティ デザイナーの値を変更、 **TypeArgument**プロパティ グリッドのコンボ ボックス。|  
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|True|反復処理を行う項目のコレクション。 設定する、 <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>、タイプ a[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]内の式、**値**ボックスに、 **ForEach\<T >** または「VB の式を入力してください」ヒント テキストで、ボックス内のアクティビティ デザイナー**値**ボックスに、**プロパティ**ウィンドウ。|  
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||各イテレーションの完了後に評価されます。 true であると評価する場合、スケジュールされた保留イテレーションはキャンセルされます。 このプロパティが設定されていない場合、スケジュールされたすべてのステートメントは、完了するまで実行されます。|  
  
 既定では、ループ反復子には、item という名前が付けられます。 反復子変数の名前を変更することができます、 **ForEach**ボックス**ParallelForEach\<T >** アクティビティ デザイナー。 ループ反復子は、<xref:System.Activities.Statements.ParallelForEach%601> アクティビティの子の式で使用できます。  
  
## <a name="see-also"></a>関連項目  
 [シーケンス](../workflow-designer/sequence-activity-designer.md)   
 [並列](../workflow-designer/parallel-activity-designer.md)   
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)