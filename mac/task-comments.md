---
title: "タスク コメント"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 674bae5b22c5b9ecc5d6fda4a9a4e30e4fcd1660
ms.sourcegitcommit: 39c525ec200c6c4ea94815567b3fad7ab14fb7b3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="task-comments"></a>タスク コメント

コードを記述する場合、完了していないコード、問題があるコード、警告の簡単な回避策などをコメントで明示的に示すのは標準的な方法です。 Visual Studio for Mac に用意されている既定の指示トークンは、TODO、HACK、FIXME、および UNDONE です。 カスタマイズしたトークンを定義するには、次の図のように、**[Visual Studio]、[ユーザー設定]、[環境]、[タスク]** の順に選択します。

 ![タスク一覧のユーザー設定](media/source-editor-image10.png)

新しいタスク コメントを追加するには、タスク キーワードを含むコメントを追加します。 例:

```
//TODO: Finish this for all properties.
```

Visual Studio for Mac では、これらのマーカーに注意を引くために、タスク一覧パッドでマーカーが強調表示されます。タスク一覧パッドは、**[表示] > [パッド] > [タスク]** で表示できます。

![タスク一覧パッド](media/source-editor-image11.png)