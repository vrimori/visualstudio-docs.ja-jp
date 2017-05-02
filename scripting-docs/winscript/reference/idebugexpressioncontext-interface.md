---
title: "IDebugExpressionContext インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpressionContext Interface
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpressionContext インターフェイス"
ms.assetid: 52af82e8-0dec-49e2-a7f3-d00f66ca1401
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionContext インターフェイス
式が評価できるコンテキストを表します。  スタック フレームのオブジェクトは、このインターフェイスを実装します。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugExpressionContext` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)|指定したテキストのデバッグの式を作成します。|  
|[IDebugExpressionContext::GetLanguageInfo](../../winscript/reference/idebugexpressioncontext-getlanguageinfo.md)|このコンテキストを所有する言語の名前と GUID を返します。|