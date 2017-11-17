---
title: "できませんへの割り当て &#39; この &#39; |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5000
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c164b9b7d2989076a9dc0ef0bafba6159bc08885
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="cannot-assign-to-39this39"></a>できませんへの割り当て &#39; この &#39;
値を代入しようとしています。**この**です。 **この**は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]いずれかを示すキーワード。  
  
-   現在、メソッドの実行オブジェクト  
  
-   現在のメソッドはありません (またはメソッドが、他のオブジェクトに属していない) 場合は、グローバル オブジェクトです。  
  
 メソッドは、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクトを介して呼び出される関数。 メソッドは、内部、**これ**キーワードによって、メソッドが呼び出されたオブジェクトへの参照は、(動作は、クラス コンス トラクターを呼び出すことによって作成されたオブジェクトである、**新しい**演算子)。  
  
 使用することができます、メソッドの内部**この**が、現在のオブジェクトを参照するために新しい値を割り当てることはできません**これ**です。  
  
### <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   割り当てるしないで**この**です。 プロパティまたはオブジェクトのインスタンスのメソッドにアクセスするには、ドット演算子を使用して (例: circle**.**半径)。  
  
    > [!NOTE]
    >  ユーザーが作成した変数の名前を付けられません**この**; は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]予約語です。  
  
## <a name="see-also"></a>関連項目  
 [このステートメント](../../javascript/reference/this-statement-javascript.md)   
 [スクリプトのトラブルシューティング](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)