---
title: "オーバーライド - コード生成 (Visual Basic) を生成します |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e8a7658ff8e2f573f2da6ff3197b6a11f3b3a0a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="generate-an-override-in-visual-basic"></a>Visual Basic では、上書きを生成します。
**新機能:**基底クラスからすぐに無効にできるメソッドのコードを生成できます。 

****基底クラスのメソッドをオーバーライドし、署名を自動的に生成します。  

**理由:**でしたメソッド シグニチャを自分で作成する、ただし、この機能は、署名を自動的に作成されます。 

**どう：**

1. 型、**オーバーライド**キーワード、その後にスペース、オーバーライドされたメソッド署名を挿入するには、IntelliSense のドロップダウン リストが表示されます。

   ![IntelliSense をオーバーライドします。](media/override_intellisense.png)

1. マウスでクリックするか、キーを押すとキーボードでナビゲートすることによって、基底クラスからをオーバーライドする方法を選択して**Enter**です。

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override_property.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override_method.png) to show or hide Methods in the list.
-->

1. 選択したメソッドまたはプロパティは、オーバーライドを実装する準備として、クラスに追加されます。

   ![結果をオーバーライドします。](media/override_result.png)

## <a name="see-also"></a>関連項目  
[コード生成 (Visual Basic)](../code-generation-vb.md) 