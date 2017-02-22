---
title: "IDebugDocumentText2 | Microsoft Docs"
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
  - "IDebugDocumentText2"
helpviewer_keywords: 
  - "IDebugDocumentText2 インターフェイス"
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはテキスト ドキュメントを表します。  
  
## 構文  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは指定する \(DE\) 必要があるソース・コードをテキスト形式である場合このインターフェイスを実装します。  これは最も一般的なケースであるためimplements しますが[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) インターフェイス`IDebugDocumentText2` のインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 `IDebugDocument2` のインターフェイスからこのインターフェイスを取得するに `QueryInterface` のメソッドを使用します。  
  
## Vtable の順序でメソッド  
 `IDebugDocument2` のインターフェイスのメソッド以外にもこのインターフェイスには次のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|ドキュメントのこの位置にあるテキストのサイズを取得します。|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|ドキュメント内の指定した位置からテキストを取得します。|  
  
## 解説  
 実装はこのインターフェイス [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) のオブジェクトの <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> のインターフェイスを提供する <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> のインターフェイスを実装する必要があります。オブジェクト。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)