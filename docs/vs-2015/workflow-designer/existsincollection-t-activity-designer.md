---
title: ExistsInCollection&lt;T&gt;アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 5c8fec33a7233960f1b90d5d4a644c8887b0f2b0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544471"
---
# <a name="existsincollectionlttgt-activity-designer"></a>ExistsInCollection&lt;T&gt;アクティビティ デザイナー
**ExistsInCollection\<T >** 作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.ExistsInCollection%601>アクティビティ。  
  
## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > アクティビティ  
 <xref:System.Activities.Statements.ExistsInCollection%601> アクティビティでは、指定した項目が特定のコレクションに存在するかどうかを確認します。  
  
### <a name="using-the-existsincollectiont-activity-designer"></a>ExistsInCollection を使用して\<T > アクティビティ デザイナー  
 **ExistsInCollection\<T >** アクティビティ デザイナーが記載されて、**コレクション**のカテゴリ、**ツールボックス**をクリックしてアクセスします。**ツールボックス**タブ[!INCLUDE[wfd2](../includes/wfd2-md.md)](または、選択**ツールバー**から、**ビュー**メニューまたは CTRL + ALT + X)。  
  
 **ExistsInCollection\<T >** からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス任意の場所、アクティビティを通常配置など内で、<xref:System.Activities.Statements.Sequence>します。 これを作成、 <xref:System.Activities.Statements.ExistsInCollection%601> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>ExistsInCollection の\<Int32 > です。 (既定で、 *TypeArgument*は**Int32**します。 プロパティ グリッドで変更できます)。<xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、 **ExistsInCollection\<T >** アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。 他のプロパティは、プロパティ グリッドで編集する必要があります。  
  
### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > のプロパティ  
 次の表に、<xref:System.Activities.Statements.ExistsInCollection%601> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ExistsInCollection%601> アクティビティの表示名。 既定値は、ExistsInCollection\<Int32 > です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|コレクションに追加する項目\<T >。 この項目の種類は*T*の種類は*TypeArgument*します。 項目を指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|項目の追加先のコレクション。 このコレクションは、型の**ICollection\<TypeArgument >。** コレクションを指定するには、プロパティ グリッドで Visual Basic の式を入力します。|  
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601> に格納される項目の T 型。 既定では、この*TypeArgument*に設定されている型**Int32**します。 型を変更するには、値を変更、 *TypeArgument*プロパティ グリッドでコンボ ボックス。|  
|<xref:System.Activities.Activity%601.Result%2A>|False|指定した項目がコレクション内に存在するかどうかを示す値。 結果にバインドする変数を指定するには、プロパティ グリッドで Visual Basic 変数を入力します。|  
  
## <a name="see-also"></a>関連項目  
 [コレクション](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T >](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T >](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)