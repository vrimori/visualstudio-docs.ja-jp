---
title: "IDebugFunctionPosition2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionPosition2"
helpviewer_keywords: 
  - "IDebugFunctionPosition2 インターフェイス"
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはソース ドキュメントの関数の抽象的な位置を表します。  
  
## 構文  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは \(DE\)ソース ドキュメント内の関数の位置を表すためこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 このインターフェイスは保留中のブレークポイントの作成に使用する [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) の共用体の一部として \(具体的には[BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) の構造体\)[BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) の構造の一部として提供されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugFunctionPosition2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|この場所は相対的です。関数の名前を取得します。|  
|[GetOffset](../Topic/IDebugFunctionPosition2::GetOffset.md)|関数の先頭からのオフセットを取得します。|  
  
## 解説  
 このインターフェイスで表される位置は特に基づいてテキスト [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) 構造です。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)