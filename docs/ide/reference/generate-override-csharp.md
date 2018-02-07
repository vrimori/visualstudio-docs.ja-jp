---
title: "上書きの生成 - コード生成 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
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
- dotnet
ms.openlocfilehash: 3801d8ce60cf87126f8894bf44c77056f996cde1
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="generate-an-override-in-c"></a>上書きの生成 (C#) #

**概要:** 基底クラスから上書きできるメソッドのコードを即座に生成します。

**条件:** 基底クラスのメソッドを上書きし、シグネチャを自動的に生成したいとき。

**理由:** メソッド シグネチャは自分でも記述できるが、この機能ではシグネチャが自動的に生成されるため。

**方法:**

1. 上書きしたメソッド シグネチャを挿入する場所に、「**override**」というキーワードを入力し、その後にスペースを入力すると、IntelliSense のドロップダウン リストが表示されます。

   ![上書き IntelliSense](media/override-intellisense-cs.png)

1. マウスでクリックするか、キーボードでナビゲートして **Enter** キーを押して、基底クラスから上書きするメソッドを選択します。

   >[!TIP]
   >* [プロパティ] アイコン ![プロパティ アイコン](media/override-property-cs.png) を使ってプロパティ一覧の表示/非表示を切り替えます。
   >* [メソッド] アイコン ![[メソッド] アイコン](media/override-method-cs.png) を使ってメソッド一覧の表示/非表示を切り替えます。

1. 選択したメソッドまたはプロパティが、上書きとしてクラスに追加され、実装する準備が整います。

   ![上書きの結果](media/override-result-cs.png)

## <a name="see-also"></a>関連項目

[コード生成](../code-generation-in-visual-studio.md)
