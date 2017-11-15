---
title: "タスク コメント"
description: 
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 973e7b627a7b5c121ff388874577fe59c45529d7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="task-comments"></a>タスク コメント

コードを記述する場合、完了していないコード、問題があるコード、警告の簡単な回避策などをコメントで明示的に示すのは標準的な方法です。 Visual Studio for Mac で提供されている既定の指示トークンは TODO、HACK、FIXME、UNDONE ですが、次の図に示すように、**[Visual Studio] > [ユーザー設定] > [環境] > [タスク]** で個人設定のトークンを定義できます。

 ![タスク一覧のユーザー設定](media/source-editor-image10.png)

新しいタスク コメントを追加するには、タスク キーワードを含むコメントを追加します。 例:

```
//TODO: Finish this for all properties.
```

Visual Studio for Mac では、これらのマーカーに注意を引くために、タスク一覧パッドでマーカーが強調表示されます。タスク一覧パッドは、**[表示] > [パッド] > [タスク]** で表示できます。

![タスク一覧パッド](media/source-editor-image11.png)