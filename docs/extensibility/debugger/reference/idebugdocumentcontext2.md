---
title: "IDebugDocumentContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2"
helpviewer_keywords: 
  - "IDebugDocumentContext2"
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDocumentContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはソース ファイルのドキュメント位置を表します。  
  
## 構文  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンはソースコードコード \(DE\) レベルのデバッグのサポートの一部としてこのインターフェイスを実装します。  ソース・コードの場所でなくこのインターフェイスはソース・コード ドキュメントを通じてコンテキストを比較しその位置に移動するためのメソッドを提供します。  
  
## 呼び出し元のメモ  
 複数のインターフェイス最もよく [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) と [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md) インターフェイスのメソッドはこのインターフェイスを返します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugDocumentContext2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetDocument](../Topic/IDebugDocumentContext2::GetDocument.md)|このドキュメントのコンテキストが含まれるドキュメントを取得します。|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|このドキュメントのコンテキストが含まれるドキュメントを表示できる名前を取得します。|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|このドキュメントのコンテキストに関連するすべてのコード コンテキスト リストを取得します。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|このドキュメントの言語のコンテキストに関連付けられているを取得します。|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|このドキュメントのコンテキストのファイルのステートメントの範囲を取得します。|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|このドキュメントのコンテキストのファイルの参照元の範囲を取得します。|  
|[比較](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|ドキュメントのコンテキストの指定された配列にこのドキュメントのコンテキストを比較します。|  
|[シーク](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|ステートメントまたは行の指定した数値ドキュメントのコンテキストを移動します。|  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)