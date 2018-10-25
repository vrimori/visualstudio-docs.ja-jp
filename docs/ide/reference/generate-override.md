---
title: Visual Studio でメソッドのオーバーライドを生成する
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 5d51139d2e5197607de2255b267c24bf2a9db2b3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919066"
---
# <a name="generate-an-override-in-visual-studio"></a>Visual Studio でオーバーライドを生成する

このコード生成は以下に適用されます。

- C#

- Visual Basic

**概要:** 基底クラスからオーバーライドできるメソッドのコードを即座に生成します。

**条件:** 基底クラスのメソッドをオーバーライドし、シグネチャを自動的に生成したいとき。

**理由:** メソッド シグネチャは自分でも記述できるが、この機能ではシグネチャが自動的に生成されるため。

## <a name="how-to"></a>方法

1. オーバーライド メソッドを挿入する位置に、「`override`」 (C# の場合) または「`Overrides`」 (Visual Basic の場合) と入力し、その後にスペースを入力します。

   - C#: 

      ![オーバーライドの IntelliSense (C#)](media/override-intellisense-cs.png)

   - Visual Basic: 

      ![オーバーライドの IntelliSense (VB)](media/override-intellisense-vb.png)

2. 基底クラスからオーバーライドするメソッドを選択します。

   > [!TIP]
   > - [プロパティ] アイコン ![プロパティ アイコン](media/override-property-cs.png) を使って、一覧でのプロパティの表示/非表示を切り替えます。
   > - [メソッド] アイコン ![[メソッド] アイコン](media/override-method-cs.png) を使って、一覧でのメソッドの表示/非表示を切り替えます。

   選択したメソッドまたはプロパティが、オーバーライドとしてクラスに追加され、実装する準備が整います。

   - C#: 

       ![オーバーライドの結果 (C#)](media/override-result-cs.png)

   - Visual Basic: 

       ![オーバーライドの結果 (VB)](media/override-result-vb.png)

## <a name="see-also"></a>関連項目

- [コード生成](../code-generation-in-visual-studio.md)