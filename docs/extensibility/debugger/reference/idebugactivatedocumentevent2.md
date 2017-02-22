---
title: "IDebugActivateDocumentEvent2 | Microsoft Docs"
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
  - "IDebugActivateDocumentEvent2"
helpviewer_keywords: 
  - "IDebugActivateDocumentEvent2 インターフェイス"
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugActivateDocumentEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンはドキュメントを \(DE\) 読み込むように要求するにはこのインターフェイスを使用します。  
  
## 構文  
  
```  
IDebugActivateDocumentEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 これはソース ファイルを開くことが必要な場合の de\-DE implements このインターフェイス。  このインターフェイスが実装され動作またはスクリプトのインタープリターの一部にデバッグ エンジンになります。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはこのインターフェイス \(`IDebugEvent2` のインターフェイスにアクセス [QueryInterface](/visual-cpp/atl/queryinterface) SDM を使用\) と同じオブジェクトで実行する必要があります。  
  
## 呼び出し元のメモ  
 DE はソース ファイルを開いている必要があるときにこのイベント オブジェクトを作成し送信します。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチしたときに送信されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugActivateDocumentEvent2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetDocument](../Topic/IDebugActivateDocumentEvent2::GetDocument.md)|ドキュメントをアクティブにする取得します。|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|ドキュメント内の場所を示すドキュメントのコンテキストを取得します。|  
  
## 解説  
 このインターフェイスを使用する一般的なシナリオは SDM に解析エラーのドキュメントに表示できるようにスクリプト DE sends このインターフェイスは解析エラーが HTML ページのスクリプト コードで発生した場合です。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)