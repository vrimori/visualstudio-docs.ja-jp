---
title: "IDebugDocumentPosition2 | Microsoft Docs"
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
  - "IDebugDocumentPosition2"
helpviewer_keywords: 
  - "IDebugDocumentPosition2 インターフェイス"
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはソース ファイルの抽象的な位置を表します。  
  
## 構文  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## 実装についてのメモ  
 Visual Studio はこのインターフェイスを実装します。  デバッグ エンジンは\(DE\) 独自のソース・コードを提供する必要がある場合はこのインターフェイスを実装します \(と同様に機能します [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) implements インターフェイス\)。  
  
## 呼び出し元のメモ  
 このインターフェイスは [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) に引数として渡されます。  また保留中のブレークポイントの作成に使用する[BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) の構造の一部である [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) の共用体 \(具体的には[BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) の構造\) の一部として提供されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugDocumentPosition2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|このドキュメントの場所を含むソース ファイルの名前を取得します。|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|含む文書を取得します。|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|この場所は特定の文書に含まれているかどうかを判定します。|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|このドキュメントの場所の範囲を取得します。|  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)