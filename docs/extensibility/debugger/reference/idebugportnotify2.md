---
title: "IDebugPortNotify2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortNotify2"
helpviewer_keywords: 
  - "IDebugPortNotify2 インターフェイス"
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugPortNotify2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスを実装するポートとデバッグするプログラムを登録するまたは登録を解除します。  
  
## 構文  
  
```  
IDebugPortNotify2 : IUnknown  
```  
  
## 実装についてのメモ  
 カスタム ポートの業者はポートからプログラムの追加と削除をサポートするにはこのインターフェイスを実装します。  これは通常同じオブジェクトに実装する [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) のインターフェイス実装されます。  
  
## 呼び出し元のメモ  
 `IDebugPort2` のインターフェイス [QueryInterface](/visual-cpp/atl/queryinterface) の呼び出しはこのインターフェイスを返します。  また[GetPortNotify](../Topic/IDebugDefaultPort2::GetPortNotify.md) の呼び出しはこのインターフェイスを返します。  デバッグ エンジンは[WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md) にパラメーターにこのインターフェイスを確認できます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugPortNotify2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|これを実行するポートとデバッグするプログラムを登録します。|  
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|これを実行するポートからデバッグするプログラムの登録を解除します。|  
  
## 解説  
 プログラムがいつ読み込むかまたはアンロードできるかデバッグ ポートを確認する方法がない場合カスタム ポートの業者はこのインターフェイスを実装する必要があります。  特定のポートを使用してデバッグに読み込まれるすべてのプログラムはこのインターフェイスを使用して追跡されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)