---
title: ブレークポイントがヒット ダイアログ ボックスの場合 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.whenbreakpointishit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
ms.assetid: 476e3d98-cf35-4338-b124-cd0f3010d854
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad979fa302a29f9d444579655e368db6da8b3e1f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805412"
---
# <a name="when-breakpoint-is-hit-dialog-box"></a>[ブレークポイントのヒット時] ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このダイアログ ボックスでは、ブレークポイントにヒットしたときに発生するアクションをカスタマイズできます。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **メッセージを出力します**  
 DebuggerDisplay 構文を使用してメッセージを出力します。 詳細については、次を参照してください。 [DebuggerDisplay 属性を使用して](../debugger/using-the-debuggerdisplay-attribute.md)します。  
  
 このテキストボックスは、$ADDRESS などの特殊なキーワードもサポートしています。これらのキーワードはキーワード自身が使用することも、DebuggerDisplay 式の中かっこ ({}) 内で使用することもできます。 使用できるキーワードはダイアログ ボックスに一覧表示されます。  
  
 **実行を継続します。**  
 このコントロールが有効になっている場合にのみ**メッセージを印刷**が選択されています。 このコントロールを選択すると、ブレークポイントにヒットしたときに、これを中断するポイントとしてではなく、プログラムの実行をトレースするためのトレースポイントとして使用できます。  
  
## <a name="see-also"></a>関連項目  
 [ブレークポイントの使用](../debugger/using-breakpoints.md)   
 [DebuggerDisplay 属性の使用](../debugger/using-the-debuggerdisplay-attribute.md)



