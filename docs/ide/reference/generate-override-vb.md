---
title: "上書きの生成 - コード生成 (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 334f5a79dad1b7d2c14768d0698797a34ad039c5
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="generate-an-override-in-visual-basic"></a>上書きの生成 (Visual Basic)
**機能:** 基底クラスから上書きできるメソッドのコードをすぐに生成できます。 

**条件:** 基底クラスのメソッドを上書きし、シグネチャを自動的に生成したいとき。  

**理由:** メソッド シグネチャは自分でも記述できるが、この機能ではシグネチャが自動的に生成されるため。 

**方法:**

1. 上書きしたメソッド シグネチャを挿入する場所に、**Overrides** キーワード、その後にスペースを入力すると、IntelliSense のドロップダウン リストが表示されます。

   ![上書き IntelliSense](media/override-intellisense-vb.png)

1. マウスでクリックするか、キーボードでナビゲートして **Enter** キーを押して、基底クラスから上書きするメソッドを選択します。

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override-property-vb.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override-method-vb.png) to show or hide Methods in the list.
-->

1. 選択したメソッドまたはプロパティが、上書きとしてクラスに追加され、実装する準備が整います。

   ![上書きの結果](media/override-result-vb.png)

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md) 