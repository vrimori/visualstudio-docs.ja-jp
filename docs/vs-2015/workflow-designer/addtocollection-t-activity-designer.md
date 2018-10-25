---
title: AddToCollection&lt;T&gt;アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 009f9f90c5cd22e5cf0da4240d008ce3dc1bb4ca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304428"
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection&lt;T&gt;アクティビティ デザイナー
**AddToCollection\<T >** 作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.AddToCollection%601>アクティビティ。  
  
## <a name="the-addtocollectiont-activity"></a>AddToCollection\<T > アクティビティ  
 <xref:System.Activities.Statements.AddToCollection%601> アクティビティでは、項目をコレクションに追加します。  
  
### <a name="using-the-addtocollectiont-activity-designer"></a>AddToCollection を使用して\<T > アクティビティ デザイナー  
 **AddToCollection\<T >** アクティビティ デザイナーが記載されて、**コレクション**のカテゴリ、**ツールボックス**をクリックしてアクセスします。**ツールボックス**のタブ、 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (または、選択**ツールバー**から、**ビュー**メニューまたは CTRL + ALT + X)。  
  
 **AddToCollection\<T >** からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス任意の場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>. これを作成、 <xref:System.Activities.Statements.AddToCollection%601> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>AddToCollection の\<Int32 > です。 (既定で、 *TypeArgument*は**Int32**します。 プロパティ グリッドで変更できます)。<xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、 **AddToCollection\<T >** アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 他のプロパティは、プロパティ グリッドで編集する必要があります。  
  
### <a name="the-addtocollectiont-properties"></a>AddToCollection\<T > のプロパティ  
 次の表に、<xref:System.Activities.Statements.AddToCollection%601> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> アクティビティの表示名。 既定値は AddToCollection\<Int32 > です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|コレクションに追加する項目\<T >。 この項目の種類は*T*、型の*TypeArgument*します。 項目を指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|項目の追加先のコレクション。 このコレクションは、型の**ICollection\<TypeArgument >** します。 コレクションを指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型。 既定では、この*TypeArgument*に設定されている型**Int32**します。 型を変更するには、値を変更、 *TypeArgument*プロパティ グリッドでコンボ ボックス。|  
  
## <a name="see-also"></a>関連項目  
 [コレクション](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T > アクティビティ デザイナー](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T >](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)