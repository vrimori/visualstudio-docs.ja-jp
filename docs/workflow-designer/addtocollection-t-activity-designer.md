---
title: "AddToCollection&lt;T&gt;アクティビティ デザイナー |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 05f7d0c9dd2be14840726bcdd3320746a1e1ca02
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection&lt;T&gt;アクティビティ デザイナー
**AddToCollection\<T >**アクティビティ デザイナーを使用して作成し、構成、<xref:System.Activities.Statements.AddToCollection%601>アクティビティ。  
  
## <a name="the-addtocollectiont-activity"></a>AddToCollection < T\>アクティビティ  
 <xref:System.Activities.Statements.AddToCollection%601> アクティビティでは、項目をコレクションに追加します。  
  
### <a name="using-the-addtocollectiont-activity-designer"></a>使用して、AddToCollection\<T > アクティビティ デザイナー  
 **AddToCollection\<T >**アクティビティ デザイナーは含まれて、**コレクション**のカテゴリ、**ツールボックス**、 をクリックしてアクセスします。**ツールボックス**のタブ、 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (または、選択**ツールバー**から、**ビュー**メニューまたは CTRL + ALT + X です)。  
  
 **AddToCollection\<T >**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**に、[!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]サーフェス任意の場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>. これを作成、 <xref:System.Activities.Statements.AddToCollection%601> 、既定値を持つアクティビティ<xref:System.Activities.Activity.DisplayName%2A>の AddToCollection < Int32\>です。 (既定では、 *TypeArgument*は**Int32**です。 プロパティ グリッドで変更できます)。<xref:System.Activities.Activity.DisplayName%2A>ヘッダーの値を編集できます、 **AddToCollection < T\>** アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 他のプロパティは、プロパティ グリッドで編集する必要があります。  
  
### <a name="the-addtocollectiont-properties"></a>AddToCollection < T\>プロパティ  
 次の表に、<xref:System.Activities.Statements.AddToCollection%601> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> アクティビティの表示名。 既定値は AddToCollection < Int32\>です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|コレクションに追加する項目\<T > です。 この項目の型は*T*、種類がある*TypeArgument*です。 項目を指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|項目の追加先のコレクション。 このコレクションの型は**ICollection < TypeArgument\>**です。 コレクションを指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型。 既定では、この*TypeArgument*に設定されている型**Int32**です。 型を変更するには、値を変更、 *TypeArgument*プロパティ グリッドのコンボ ボックスにします。|  
  
## <a name="see-also"></a>参照  
 [コレクション](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T > アクティビティ デザイナー](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T >](../workflow-designer/removefromcollection-t-activity-designer.md)