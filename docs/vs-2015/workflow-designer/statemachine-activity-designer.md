---
title: StateMachine アクティビティ デザイナー |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- StateMachine Designer
- System.Activities.Statements.StateMachine.UI
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: 5
author: steved0x
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 1f768142ce3cf71b254e6740a87895f5626372fa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47534875"
---
# <a name="statemachine-activity-designer"></a>StateMachine アクティビティ デザイナー
<xref:System.Activities.Statements.StateMachine> アクティビティには状態のコレクションが含まれており、一般的なステート マシン パラダイムを使用してワーク フローをモデル化します。  
  
## <a name="using-the-statemachine-activity-designer"></a>StateMachine アクティビティ デザイナーの使用  
 追加する、<xref:System.Activities.Statements.StateMachine>アクティビティをドラッグ、 **StateMachine**からアクティビティ デザイナー、**ステート マシン**のセクション、**ツールボックス**にドロップし、 [!INCLUDE[wfd1](../includes/wfd1-md.md)]画面。 この子の状態を追加する<xref:System.Activities.Statements.StateMachine>アクティビティをドラッグ、<xref:System.Activities.Statements.State>または<xref:System.Activities.Core.Presentation.FinalState>から、**ツールボックス**にドロップし、 **StateMachine**します。  
  
### <a name="statemachine-activity-properties-in-the-workflow-designer"></a>ワークフロー デザイナーでの StateMachine アクティビティのプロパティ  
 次の表に、ワークフロー デザイナーを使用して設定できる <xref:System.Activities.Statements.StateMachine> のプロパティと、デザイナーでのその使用方法を示します。 これらのプロパティは、プロパティ グリッドで編集できます。また、その一部はデザイナー画面で編集できます。  
  
|プロパティ名|必須|使用方法|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|ヘッダーの <xref:System.Activities.Statements.StateMachine> アクティビティ デザイナーの表示名を指定します。 既定値は**StateMachine**します。 この値は、プロパティ グリッドで編集することも、アクティビティ デザイナーのヘッダーで直接編集することもできます。 <xref:System.Activities.Activity.DisplayName%2A> は、ワークフロー デザイナーの上部に表示される階層リンク バーで使用されます。<br /><br /> <xref:System.Activities.Activity.DisplayName%2A> は必須ではありませんが、使用することをお勧めします。|  
  
## <a name="see-also"></a>関連項目  
 [フローチャート](../workflow-designer/flowchart-activity-designer.md)   
 [制御フロー](../workflow-designer/control-flow-activity-designers.md)