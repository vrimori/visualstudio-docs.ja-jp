---
title: "IDebugDocumentTextEvents2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents2 インターフェイス"
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ エンジンが提供するソース ドキュメントへの変更に関する Visual Studio を通知するために使用されます。  
  
## 構文  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements ソース・コードに変更を加えることをサポートするインターフェイス。この  このインターフェイスは同じオブジェクトでは通常を実装する [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) のインターフェイス実装されます。  
  
## 呼び出し元のメモ  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] は <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> のメソッドを呼び出すことによってこのインターフェイスを取得します。  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> のインターフェイスは呼び出しから <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> のメソッドを派生します。  <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> のインターフェイスは [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) のインターフェイス [QueryInterface](/visual-cpp/atl/queryinterface) のメソッドを呼び出すことになります。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugDocumentTextEvents2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|文書全体が破棄されたことを示します。|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|テキストが文書に挿入デバッグのパッケージに通知します。|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|テキストが文書から削除されたデバッグのパッケージに通知します。|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|テキストが文書に置き換えられたデバッグのパッケージに通知します。|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|テキスト属性がドキュメントに更新されデバッグのパッケージに通知します。|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|ドキュメントの属性が更新されイベントの受信側に通知します。|  
  
## 解説  
 独自のドキュメントを使用する `IDebugDocumentTextEvent2` のインターフェイスを提供するエンジンだけをデバッグします。  この例ではスクリプトのデバッグ エンジンです。  スクリプトを解釈するプロセスではすべてのディスク ファイルにないのでde\-DE だけが検証された新しいソース・コードを生成できます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)