---
title: "方法: 階層リンク バー ナビゲーションを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 95e79ab384c6311aa17f2592b514d62b899b8b6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-breadcrumb-navigation"></a>階層リンク バーを使用する方法
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]に表示されるアクティビティのセットを変更する主な方法は、次の 3 つです。  
  
1.  ダブルクリックして、子アクティビティにドリル ダウンする。  
  
2.  階層リンク バーのボタンをクリックして、先祖アクティビティに移動する。  
  
3.  アクティビティを直接展開するか、折りたたむ。  
  
### <a name="using-breadcrumb-navigation"></a>階層リンク バーの使用  
  
1.  [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]のアクティビティをダブルクリックして、クリックしたアクティビティのルート アクティビティを変更します。 クリックしたアクティビティはルートで完全に展開され、その先祖が階層リンク バーに表示されます。 これは、アクティビティのドリル インまたはドリル アウトと呼ばれることがあります。  
  
2.  現在のルート アクティビティの先祖に移動するには、階層リンク バーのアクティビティをクリックします。  
  
### <a name="expanding-or-collapsing-an-activity-in-place"></a>アクティビティの直接の展開または折りたたみ  
  
1.  アクティビティのシェブロンをクリックすると、その場でアクティビティが展開されるか、折りたたまれます。  
  
2.  ボタンのクリックによって展開の状態が変更されると、展開の新しい状態が XAML に保存されます。  
  
    > [!WARNING]
    >  アクティビティには、その場で展開できないものもあります。 アクティビティをその場で展開できない状況は 2 つ考えられます。親アクティビティがその子アクティビティに対して、その場での展開を許可していない場合 (たとえば、フローチャート内のアクティビティをその場で展開できない) と、アクティビティ デザイナー自体でその場での展開が禁止されている場合です。 [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]に含まれるアクティビティ デザイナーでは、その場での展開は禁止されていませんが、一部のカスタム アクティビティは、この理由で展開できない場合があります。  
  
### <a name="expanding-all-or-collapsing-all-activities"></a>すべてのアクティビティの展開または折りたたみ  
  
1.  使用して、**すべて展開**と**すべて折りたたみ**を展開または折りたたみの現在の階層リンク バー ルートの下のすべてのユーザー インターフェイスでボタン。 "すべて展開" および "すべて折りたたみ" はグローバル状態であることに注意してください。 つまり、階層リンク バー ナビゲーション、すべての展開を使用してルート アクティビティを変更またはすべての状態の折りたたみを行うときに永続化することをクリックするまで**復元**です。  
  
2.  クリックすることができますが、すべての展開を適用した場合、またはすべての状態を折りたたむ後、**復元**いた各アクティビティに適用されていた状態を見るに戻るに表示されるボタンをクリックします。  
  
    > [!WARNING]
    >  アクティビティなど<xref:System.Activities.Statements.Flowchart>、招き場で展開のうち、機能に関連付けられている、**すべて展開**と**すべて折りたたむ**ボタンが無効になって、**フローチャート**デザイナー。 [!INCLUDE[crabout](../test/includes/crabout_md.md)]**フローチャート**デザイナーを参照してください、[フローチャート](../workflow-designer/flowchart-activity-designer.md)トピックです。  
  
    > [!WARNING]
    >  [すべて展開] 特殊効果があります**スイッチ**と**TryCatch**アクティビティ デザイナー。 クリックすると、**すべて展開**、すべての switch ケースおよびすべての catch または finally ブロックが表示されます。 クリックすると**復元**または**すべて折りたたむ**個別の case/block をその内容を表示する既定の状態をクリックしてこれらのデザイナーを返します。