---
title: "IDebugDocumentPositionOffset2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugDocumentPositionOffset2 インターフェイス"
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

文字のオフセットとしてソース ファイルの位置を表します。  
  
## 構文  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## 実装についてのメモ  
 IDE で実行されデバッグ エンジンによって実装されます。  
  
## メソッド  
 次の表は `IDebugDocumentPositionOffset2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetRange](../Topic/IDebugDocumentPositionOffset2::GetRange.md)|現在のドキュメント位置の範囲を取得します。|  
  
## 解説  
 これはドキュメントの先頭からのオフセット `char` の [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) と同じ情報を返します。  これは通常返される行と列の情報ではなくディスク文字列の先頭次元配列になるようにドキュメントを示します。  
  
## 必要条件  
 ヘッダー : Msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)