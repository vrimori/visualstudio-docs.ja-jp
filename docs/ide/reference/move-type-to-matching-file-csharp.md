---
title: "一致するファイルへの型の移動 - リファクタリング (C#) | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 4b7b9b1ba52bed5d2bdf042db0149d799c489a7d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="move-a-type-to-a-matching-file-in-c"></a>一致するファイルへの型の移動 (C#) #

**機能:** 選択した型を同じ名前の別のファイルに移動できます。

**条件:** 同じファイルに複数のクラス、構造体、インターフェイスなどがあり、分離したいとき。

**理由:** 同じファイルに複数の型を配置すると、これらの型を検索しづらくなります。  型を同じ名前のファイルに移動することで、コードが読みやすくナビゲートしやすくなります。

**方法:**

1. 移動する型の名前を強調表示するか、名前の内側にテキスト カーソルを置きます。

   ![強調表示されたコード](media/movetype-highlight-cs.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップ から **[型を *TypeName*.cs に移動]** を選択します。ここで、*TypeName* は選択した型の名前です。
   * **マウス**
     * コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップ から **[型を *TypeName*.cs に移動]** を選択します。ここで、*TypeName* は選択した型の名前です。

   型が、すぐに、ソリューション内のその名前の新しいファイルに移動します。

   ![インラインの結果](media/movetype-result-cs.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)