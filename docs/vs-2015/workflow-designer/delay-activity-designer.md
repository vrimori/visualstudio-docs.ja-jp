---
title: アクティビティ デザイナーを遅延 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Delay.UI
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: b861eb70315b2a734cdedb4346e0bcd9f2143678
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49282764"
---
# <a name="delay-activity-designer"></a>Delay アクティビティ デザイナー
**遅延**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.Delay>アクティビティ。  
  
## <a name="the-delay-activity"></a>Delay アクティビティ  
 <xref:System.Activities.Statements.Delay> アクティビティで、ワークフローの実行を、指定した時間だけ遅らせます。  
  
### <a name="using-the-delay-activity-designer"></a>Delay アクティビティ デザイナーの使用  
 **遅延**アクティビティ デザイナーが記載されて、**プリミティブ**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス**のタブ、 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (または、選択**ツールバー**から、**ビュー**メニューのまたは CTRL + ALT + X)。  
  
 **遅延**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス任意の場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>します。 この操作により、Delay という既定の <xref:System.Activities.Statements.Delay> を持つ <xref:System.Activities.Activity.DisplayName%2A> アクティビティが作成されます。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーで編集できる、**遅延**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。  
  
### <a name="the-delay-properties"></a>Delay のプロパティ  
 次の表に、<xref:System.Activities.Statements.Delay> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できます。また、その一部は[!INCLUDE[wfd2](../includes/wfd2-md.md)]のデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Delay> アクティビティの表示名。 既定値は Delay です。 <xref:System.Activities.Activity.DisplayName%2A> 値は必須ではありませんが、使用することをお勧めします。|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|ワークフローの実行を遅らせる時間の長さ。 このプロパティは、プロパティ グリッドで設定します。 時間の長さを指定するには、00:00:00 という形式のリテラル <xref:System.TimeSpan>、または Visual Basic の式を入力します。|  
  
## <a name="see-also"></a>関連項目  
 [プリミティブ](../workflow-designer/primitives-activity-designers.md)   
 [割り当てる](../workflow-designer/assign-activity-designer.md)   
 [Delay アクティビティ デザイナー](../workflow-designer/delay-activity-designer.md)   
 [メソッドの呼び出し](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)