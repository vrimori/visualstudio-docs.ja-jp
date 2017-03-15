---
title: "IDebugDocument2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocument2"
helpviewer_keywords: 
  - "IDebugDocument2 インターフェイス"
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDocument2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはソース ドキュメントを表します。  
  
## 構文  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## 実装についてのメモ  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] はこのインターフェイスを実装します。  デバッグ エンジンは \(DE\)ソース・コードを指定する必要がありソースがディスク上にない場合このインターフェイスを実装できます。  この場合de\-DE は[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) と [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) のインターフェイス [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) と [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) のインターフェイスやそのほかのメソッドを実装します。  
  
## 呼び出し元のメモ  
 `IDebugDocumentContext2` `IDebugDisassemblyStream2` `IDebugDocumentPosition2` と `IDebugActivateDocumentEvent2` インターフェイスのメソッドはこのインターフェイスを返します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugDocument2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|複数のフォームの 1 種類のドキュメントの名前を取得します。|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|ドキュメントのクラス ID を取得します。|  
  
## 解説  
 このインターフェイスはにのみ機能します supplies ソース・コードが実行されます。  たとえばHTML ページのスクリプトをデバッグする場合はソースやディスク ファイルとして存在しない動的にダウンロードされが生成されソース・コード supplies します。  従来の言語を設定しC\+\+ などのデバッグするときにはこのインターフェイスを実装する必要はありません。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../Topic/IDebugActivateDocumentEvent2::GetDocument.md)   
 [GetDocument](../Topic/IDebugDocumentContext2::GetDocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)