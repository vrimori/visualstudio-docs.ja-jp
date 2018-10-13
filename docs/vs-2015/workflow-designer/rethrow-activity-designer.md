---
title: Rethrow アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 724e0b69fb14735682d437c9f21906560b15a590
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49280684"
---
# <a name="rethrow-activity-designer"></a>Rethrow アクティビティ デザイナー
**を再スロー**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.Rethrow>アクティビティ。  
  
## <a name="the-rethrow-activity"></a>Rethrow アクティビティ  
 <xref:System.Activities.Statements.Rethrow> アクティビティでは、以前にスローされた例外をスローします。 このアクティビティは、<xref:System.Activities.Statements.Catch> アクティビティの <xref:System.Activities.Statements.TryCatch> ハンドラーでのみ使用できます。  
  
### <a name="using-the-rethrow-activity-designer"></a>ReThrow アクティビティ デザイナーの使用  
 **を再スロー**アクティビティ デザイナーが記載されて、**エラー処理**のカテゴリ、**ツールボックス**をクリックしてアクセスする、**ツールボックス** タブの左側にある、 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (または、選択**ツールバー**から、**ビュー**メニューまたは CTRL + ALT + X)。  
  
 **を再スロー**からアクティビティ デザイナーをドラッグすることができます、**ツールボックス**ドロップ、[!INCLUDE[wfd2](../includes/wfd2-md.md)]サーフェス任意の場所、アクティビティを通常配置など内、<xref:System.Activities.Statements.Sequence>します。 これを作成、 <xref:System.Activities.Statements.Rethrow> 、既定値は、アクティビティ**DisplayName** Throw の。 <xref:System.Activities.Activity.DisplayName%2A>のヘッダーに値を編集できる、**を再スロー**アクティビティ デザイナーまたは、 **DisplayName**プロパティ グリッドのボックスです。  
  
### <a name="the-rethrow-properties"></a>Rethrow のプロパティ  
 次の表に、<xref:System.Activities.Statements.Rethrow> のプロパティと、デザイナーでのその使用方法を示します。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Rethrow> アクティビティの表示名を指定します (省略可能)。 既定値は Rethrow です。|  
  
## <a name="see-also"></a>関連項目  
 [コレクション](../workflow-designer/collection-activity-designers.md)   
 [スローします。](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)