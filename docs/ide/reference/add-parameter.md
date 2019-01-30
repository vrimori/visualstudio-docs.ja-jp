---
title: メソッドにパラメーターを追加するクイック アクション
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7de4c4aec07a3151332c199749bef4409966b3e1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929888"
---
# <a name="add-a-parameter-to-a-method-using-a-quick-action"></a>クイック アクションを使用してメソッドにパラメーターを追加する

このコード生成は以下に適用されます。

- C#

- Visual Basic

**概要:** 使用量に基づいて、メソッドにパラメーターを自動的に追加することができます。

**条件:** メソッドにパラメーターを追加し、それを自動的に正しく宣言する必要がある場合。

**理由:** 呼び出す前にメソッドの宣言にパラメーターを追加することもできますが、この機能ではそれがメソッドの呼び出しに基づいて自動的に追加されます。

## <a name="how-to-use-it"></a>使用方法

1. メソッドの呼び出しに追加の引数を追加します。

   呼び出す場所で、メソッドの名前の下に赤い "波線" が表示されます。

2. [クイック アクション] メニューが表示されるまで赤い "波線" の上にポインターを合わせます。 [クイック アクション] メニューの**下矢印**を選択した後、**[パラメーターを [メソッド] に追加する]** を選択します。

   ![Visual Studio でのメソッドにパラメーターを追加するクイック アクション](media/add-parameter-to-method.png)

   > [!TIP]
   > また、[クイック アクション] メニューにアクセスするには、メソッドの呼び出しの行にカーソルを合わせて **Ctrl**+**.** キーを押すか、 または、ファイルの余白の電球アイコンを選択するという方法もあります。

   Visual Studio によって、メソッドの宣言に新しいパラメーターが追加されます。

> [!NOTE]
> メソッドに対するその他の呼び出しがある場合、このクイック アクションを使用した後はそれらでエラーが発生する場合があります。新しく追加されたパラメーターの引数を指定していないためです。

## <a name="see-also"></a>関連項目

- [コンストラクターにパラメーターを追加する](generate-constructor.md#addparameter)