---
title: RemoveFromCollection&lt;T&gt;アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 341ed640666cc4501ac8917b568bf3f41b89b823
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49170926"
---
# <a name="removefromcollectionlttgt-activity-designer"></a>RemoveFromCollection&lt;T&gt;アクティビティ デザイナー
**RemoveFromCollection\<T >** 作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.RemoveFromCollection%601>アクティビティ。  
  
## <a name="the-removefromcollectiont-activity"></a>RemoveFromCollection\<T > アクティビティ  
 <xref:System.Activities.Statements.RemoveFromCollection%601> アクティビティは、指定した項目を特定のコレクションから削除します。  
  
### <a name="using-the-removefromcollectiont-activity-designer"></a>RemoveFromCollection を使用して\<T > アクティビティ デザイナー  
 **RemoveFromCollection\<T >** アクティビティ デザイナーが記載されて、**コレクション**のカテゴリ、**ツールボックス**をクリックしてアクセスするが、**ツールボックス**タブ[!INCLUDE[wfd2](../includes/wfd2-md.md)](または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X)。  
  
 **RemoveFromCollection\<T >** からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス任意の場所、アクティビティを通常配置など内で、<xref:System.Activities.Statements.Sequence>します。 これを作成、 <xref:System.Activities.Statements.RemoveFromCollection%601> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>RemoveFromCollection の\<Int32 > です。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、 **RemoveFromCollection\<T >** アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 他のプロパティは、プロパティ グリッドで編集する必要があります。  
  
### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection\<T > のプロパティ  
 次の表に、<xref:System.Activities.Statements.RemoveFromCollection%601> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.RemoveFromCollection%601> アクティビティの省略可能な表示名。 既定値は、RemoveFromCollection\<Int32 > です。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|追加する項目、**コレクション\<T >** します。 この項目の種類は*T*、型の*TypeArgument*します。 項目を指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|項目の追加先のコレクション。 このコレクションは、型の**ICollection\<TypeArgument >。** コレクションを指定するには、プロパティ グリッドで Visual Basic の式に入力します。|  
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型。 既定では、この*TypeArgument*に設定されている型**Int32**します。 型を変更するには、値を変更、 *TypeArgument*プロパティ グリッドでコンボ ボックス。|  
|<xref:System.Activities.Activity%601.Result%2A>|False|指定した項目がコレクションから削除されたかどうかを示す値。 結果にバインドする変数を指定するには、プロパティ グリッドで変数を入力します。|  
  
## <a name="see-also"></a>関連項目  
 [コレクション](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)