---
title: "IDebugDisassemblyStream2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2 インターフェイス"
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDisassemblyStream2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは命令ストリームを表します。  
  
## 構文  
  
```  
IDebugDisassemblyStream2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンはプログラム コードの作成をサポートするにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) のメソッドの呼び出しこのインターフェイス。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugDisassemblyStream2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|構成ストリームの現在位置から始めて命令を読み取ります。|  
|[シーク](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|指定した位置に対する命令の指定した数値の逆アセンブル\] ストリームの読み取りポインターを移動します。|  
|[GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)|特定のコード コンテキストのコード位置の識別子を返します。|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|コード識別子の指定位置に対応するコード コンテキスト オブジェクトを返します。|  
|[GetCurrentLocation](../Topic/IDebugDisassemblyStream2::GetCurrentLocation.md)|現在のコード位置を表すコード位置の識別子を返します。|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|ソース ドキュメントをアセンブルこのストリームに関連付けられているを取得します。|  
|[GetScope](../Topic/IDebugDisassemblyStream2::GetScope.md)|この構成ストリームの範囲を取得します。|  
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|この構成ストリームのサイズを取得します。|  
  
## 解説  
 構成ストリームは空間内のアドレス空間または関数またはモジュールを表すために作成できます。  各命令は [読み取り](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) メソッドの呼び出しによって返される [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) の構造体によって表されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)