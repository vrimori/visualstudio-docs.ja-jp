---
title: "IDebugExpression インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugExpression インターフェイス"
ms.assetid: 36c00ffb-7160-4c30-a2c9-c9d70c8213cd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression インターフェイス
非同期に評価される式を表します。  スクリプト エンジンは通常、このインターフェイスを実装します。  デバッガーの IDE は、通常、即時実行ウィンドウまたはウォッチ ウィンドウを有効にするには、このインターフェイスを使用します。  
  
> [!NOTE]
>  `IDebugExpression` のインターフェイスは、スタック フレームでのみ使用できます。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugExpression` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugExpression::Start](../../winscript/reference/idebugexpression-start.md)|式の評価を開始します。|  
|[IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)|式を中止します。|  
|[IDebugExpression::QueryIsComplete](../../winscript/reference/idebugexpression-queryiscomplete.md)|操作が完了したかどうかを判定します。|  
|[IDebugExpression::GetResultAsString](../../winscript/reference/idebugexpression-getresultasstring.md)|文字列演算および演算の戻り値として式の評価の結果を返します。|  
|[IDebugExpression::GetResultAsDebugProperty](../../winscript/reference/idebugexpression-getresultasdebugproperty.md)|デバッグのプロパティと動作の戻り値として式の評価の結果を返します。|