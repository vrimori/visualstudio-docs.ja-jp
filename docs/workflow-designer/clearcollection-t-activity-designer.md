---
title: "ClearCollection&lt;T&gt;アクティビティ デザイナー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 54cac37194a3b96d464b886c14bfbbbde4a1f861
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="clearcollectionlttgt-activity-designer"></a>ClearCollection&lt;T&gt;アクティビティ デザイナー
**ClearCollection\<T >**アクティビティ デザイナーを使用して作成し、構成、<xref:System.Activities.Statements.ClearCollection%601>アクティビティ。  
  
## <a name="the-clearcollectiont-activity"></a>ClearCollection < T\>アクティビティ  
 <xref:System.Activities.Statements.ClearCollection%601> アクティビティで、指定したすべての項目のコレクションをクリアします。  
  
### <a name="using-the-clearcollectiont-activity-designer"></a>使用して、ClearCollection\<T > アクティビティ デザイナー  
 **ClearCollection\<T >**アクティビティ デザイナーは含まれて、**コレクション**のカテゴリ、**ツールボックス**、 をクリックしてアクセスします。**ツールボックス**のタブ、 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (または、選択**ツールバー**から、**ビュー**メニューまたは CTRL + ALT + X です)。  
  
 **ClearCollection\<T >**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]サーフェス任意の場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>. これを作成、 <xref:System.Activities.Statements.ClearCollection%601> 、既定値を持つアクティビティ<xref:System.Activities.Activity.DisplayName%2A>の ClearCollection < Int32\>です。 (既定では、 *TypeArgument*は**Int32**です。 プロパティ グリッドで変更できます)。<xref:System.Activities.Activity.DisplayName%2A>ヘッダーの値を編集できます、 **ClearCollection < T\>** アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 他のプロパティは、プロパティ グリッドで編集する必要があります。  
  
### <a name="the-clearcollectiont-properties"></a>ClearCollection < T\>プロパティ  
 次の表に、<xref:System.Activities.Statements.ClearCollection%601> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ClearCollection%601> アクティビティの表示名を指定します (省略可能)。 既定値は ClearCollection < Int32\>です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|クリアする項目のコレクションを指定します。 このコレクションの型は**ICollection\<TypeArgument >。** コレクションを指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型を指定します。 既定では、この*TypeArgument*に設定されている型**Int32**です。 型を変更するには、値を変更、 *TypeArgument*プロパティ グリッドのコンボ ボックスにします。|  
  
## <a name="see-also"></a>参照  
 [コレクション](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)