---
title: "オーバーライド - コード生成 (c#) を生成します |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f7193722e7ec1bee7c63e2495ed2d07155cc663b
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/29/2017
---
# <a name="generate-an-override-in-c"></a>C# では、上書きを生成します。 #

**新機能:**基底クラスからすぐにオーバーライドできるすべてのメソッドのコードを生成することができます。

**基底**クラスのメソッドをオーバーライドし、署名を自動的に生成します。

**理由:**でしたメソッド シグニチャを自分で作成する、ただし、この機能は、署名を自動的に作成されます。

**どう：**

1. 型、**オーバーライド**キーワード、その後にスペース、オーバーライドされたメソッド署名を挿入するには、IntelliSense のドロップダウン リストが表示されます。

   ![IntelliSense をオーバーライドします。](media/override_intellisense.png)

1. マウスでクリックするか、キーを押すとキーボードでナビゲートすることによって、基底クラスからをオーバーライドする方法を選択して**Enter**です。

   >[!TIP]
   >* プロパティ アイコンを使用します。 ![プロパティ アイコン](media/override_property.png) 非表示のプロパティ一覧にします。
   >* [メソッド] アイコンを使用します。 ![[メソッド] アイコン](media/override_method.png) 表示を切り替える、リスト内のメソッドを非表示にします。

1. 選択したメソッドまたはプロパティは、オーバーライドを実装する準備として、クラスに追加されます。

   ![結果をオーバーライドします。](media/override_result.png)

## <a name="see-also"></a>参照

[コード生成 (C#)](../code-generation-csharp.md)
