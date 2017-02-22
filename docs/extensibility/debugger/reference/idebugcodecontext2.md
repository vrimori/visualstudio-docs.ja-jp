---
title: "IDebugCodeContext2 | Microsoft Docs"
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
  - "IDebugCodeContext2"
helpviewer_keywords: 
  - "IDebugCodeContext2 インターフェイス"
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCodeContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはコード命令の開始位置を表します。  今日ほとんどのランタイム アーキテクチャのコードはプログラムの実行コンテキストのストリームのアドレスと考えることができます。  
  
## 構文  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## 実装についてのメモ  
 デバッグ エンジンはドキュメントの場所にコード命令の位置を関連付けるにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 多くのインターフェイスのメソッドはこのインターフェイスは最も一般 [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md) 返します。  また[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) インターフェイスと広く使用されてブレークポイントの解決方法についてで。  
  
## Vtable の順序でメソッド  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) のインターフェイスのメソッド以外にもこのインターフェイスには次のメソッドを実行します :  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetDocumentContext](../Topic/IDebugCodeContext2::GetDocumentContext.md)|アクティブなコード コンテキストに対応するドキュメントのコンテキストを取得します。|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|このコード コンテキストの言語の情報を取得します。|  
  
## 解説  
 `IDebugCodeContext2` インターフェイスとインターフェイス [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) の間の主な違いは `IDebugCodeContext2` が常について配置されます。  これは `IDebugMemoryContext2` が実行時アーキテクチャのメモリの各バイトを指す場合があります。`IDebugCodeContext2` が命令の開始点としていることを意味します。  `IDebugCodeContext2` は基本ストレージのサイズ \(通常はバイト\) ではなく命令ずつインクリメントされます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../Topic/IDebugThread2::CanSetNextStatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../Topic/IDebugStackFrame2::GetCodeContext.md)   
 [次へ](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)