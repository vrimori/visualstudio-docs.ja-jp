---
title: "'This' に割り当てることはできません |Microsoft Docs"
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f47778075b0395e4f0791d8f485188d40fab87a4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344175"
---
# <a name="cannot-assign-to-this"></a>'this' に割り当てることはできません。
**this** に値を割り当てようとしました。 **this**は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]キーワードのいずれかを参照します。

- 現在、メソッドを実行するオブジェクト

- 現在のメソッドはありません (または、メソッドが、他のオブジェクトに属していない) 場合は、グローバル オブジェクトです。

メソッドは、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクトを介して呼び出される関数。 メソッド内で、**this**キーワードによって、メソッドが呼び出されたオブジェクトへの参照は、(クラスのコンス トラクターを呼び出すことによって作成されたオブジェクトである、**新しい**演算子)。

メソッド内では、**this** を使用して現在のオブジェクトを参照できますが、**this** に新しい値を割り当てることはできません。

## <a name="to-correct-this-error"></a>このエラーを解決するには

- **this**に割り当てないでください。 プロパティまたはオブジェクトのインスタンスのメソッドにアクセスするには、ドット演算子(例: **circle.radius**)を使用してます 。

  > [!NOTE]
  > ユーザーが作成した変数には**this**を指定することはできません。**this**; は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]予約語。

## <a name="see-also"></a>関連項目

- [this ステートメント](../../javascript/reference/this-statement-javascript.md)
- [スクリプトのトラブルシューティング](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)
