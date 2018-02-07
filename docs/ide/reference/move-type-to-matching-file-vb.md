---
title: "一致するファイルへの型の移動 - リファクタリング (Visual Basic) | Microsoft Docs"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 510b984ad2de9476d53e9a5a4bcd667f393d3d4b
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2018
---
# <a name="move-type-to-a-matching-file-in-visual-basic"></a>一致するファイルへの型の移動 (Visual Basic)

**機能:** 選択した型を同じ名前の別のファイルに移動できます。

**条件:** 同じファイルに複数のクラス、構造体、インターフェイスなどがあり、分離したいとき。  

**理由:** 同じファイルに複数の型を配置すると、これらの型を検索しづらくなります。  型を同じ名前のファイルに移動することで、コードが読みやすくナビゲートしやすくなります。

**方法:**

1. 移動する型の名前を強調表示するか、名前の内側にテキスト カーソルを置きます。

   ![強調表示されたコード](media/movetype-highlight-vb.png)

1. 次に、以下のいずれかを実行します。
   * **キーボード**
     * **Ctrl + .** キーを押して、 **[クイック アクションとリファクタリング]** メニューをトリガーし、[プレビュー] ウィンドウ ポップアップから **[型を *TypeName*.vb に移動]** を選択します。ここで、*TypeName* は選択した型の名前です。
   * **マウス**
     * コードを右クリックして **[クイック アクションとリファクタリング]** メニューを選択し、[プレビュー] ウィンドウ ポップアップから **[型を *TypeName*.vb に移動]** を選択します。ここで、*TypeName* は選択した型の名前です。

   型が、すぐに、ソリューション内のその名前の新しいファイルに移動します。

   ![インラインの結果](media/movetype-result-vb.png)

## <a name="see-also"></a>関連項目

[リファクタリング](../refactoring-in-visual-studio.md)