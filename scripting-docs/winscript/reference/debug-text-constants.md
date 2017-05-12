---
title: "DEBUG_TEXT 定数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# DEBUG_TEXT 定数
[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md) 中に使用されます。  
  
## 構文  
  
```  
typedef DWORD DEBUG_TEXT;  
  
```  
  
## 定数  
  
|定数|値|説明|  
|--------|-------|--------|  
|DWORD DEBUG\_TEXT\_ISEXPRESSION|0x00000001|テキストがステートメントではなく式であることを示します。  このフラグは、一部の言語によるテキストの解析方法に影響する場合があります。|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|戻り値が使用できる場合、その値は呼び出し元によって使用されます。|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|副作用を許可しません。  このフラグが設定されている場合は、ランタイム状態が式の評価によって変更されることはありません。|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|テキスト評価中のブレークポイントを許可します。  このフラグが設定されていない場合は、テキストの評価中、ブレークポイントが無視されます。|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|テキスト評価中のエラー レポートを許可します。  このフラグが設定されていない場合は、評価中、エラーがホストにレポートされません。|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|式がコード コンテキストに評価されることを示します。式自体は実行されません。|  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)