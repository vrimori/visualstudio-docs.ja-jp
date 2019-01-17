---
title: ブレークポイントがヒット ダイアログ ボックスの場合 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 560a79892ee50f3d151971f46bcc2c2b7f205d3f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53845617"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>[ブレークポイントのヒット時] ダイアログ ボックス
このダイアログ ボックスでは、ブレークポイントにヒットしたときに発生するアクションをカスタマイズできます。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **メッセージを表示する**  
 DebuggerDisplay 構文を使用してメッセージを出力します。 詳細については、次を参照してください。 [DebuggerDisplay 属性を使用して](../debugger/using-the-debuggerdisplay-attribute.md)します。  
  
 このテキストボックスは、$ADDRESS などの特殊なキーワードもサポートしています。これらのキーワードはキーワード自身が使用することも、DebuggerDisplay 式の中かっこ ({}) 内で使用することもできます。 使用できるキーワードはダイアログ ボックスに一覧表示されます。  
  
 **続けて実行する**  
 このコントロールは、**[メッセージを表示する]** が選択されている場合にだけ有効になります。 このコントロールを選択すると、ブレークポイントにヒットしたときに、これを中断するポイントとしてではなく、プログラムの実行をトレースするためのトレースポイントとして使用できます。  
  
## <a name="see-also"></a>「  
 [ブレークポイントの使用](../debugger/using-breakpoints.md)   
 [DebuggerDisplay 属性の使用](../debugger/using-the-debuggerdisplay-attribute.md)