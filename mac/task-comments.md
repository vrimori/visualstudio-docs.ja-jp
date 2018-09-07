---
title: タスク コメント
description: コードにタスク コメントを追加する
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 562DCB46-D8FA-4DC4-AAEA-F274448C4CD2
ms.openlocfilehash: 44d82becfbf3a16ccd2158ac05e171e8530cd721
ms.sourcegitcommit: 2597236a481afbaf1ad4915743898ee1aee49760
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/10/2018
ms.locfileid: "43224113"
---
# <a name="task-comments"></a>タスク コメント

コードを記述する場合、完了していないコード、問題があるコード、警告の簡単な回避策などをコメントで明示的に示すのは標準的な方法です。 Visual Studio for Mac に用意されている既定の指示トークンは、TODO、HACK、FIXME、および UNDONE です。 カスタマイズしたトークンを定義するには、次の図のように、**[Visual Studio]、[ユーザー設定]、[環境]、[タスク]** の順に選択します。

 ![タスク一覧のユーザー設定](media/source-editor-image10.png)

新しいタスク コメントを追加するには、タスク キーワードを含むコメントを追加します。 例:

```csharp
//TODO: Finish this for all properties.
```

Visual Studio for Mac では、これらのマーカーに注意を引くために、タスク一覧パッドでマーカーが強調表示されます。タスク一覧パッドは、**[表示] > [パッド] > [タスク]** で表示できます。

![タスク一覧パッド](media/source-editor-image11.png)