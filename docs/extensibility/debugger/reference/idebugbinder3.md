---
title: "IDebugBinder3 | Microsoft Docs"
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
  - "IDebugBinder3"
helpviewer_keywords: 
  - "IDebugBinder3 インターフェイス"
ms.assetid: 92353a74-dc74-4f93-8762-61d6b220478c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、種類、エイリアス、およびカスタム ビジュアライザー サービスにアクセスを提供します。  
  
## 構文  
  
```  
IDebugBinder3 : IDebugBinder  
```  
  
## 実装についてのメモ  
 デバッグ エンジンでは、エイリアス、カスタムのビジュアライザー サービス、およびオブジェクトの種類の情報へのアクセスをサポートするには、このインターフェイスを実装します。  
  
## 呼び出し元のノート  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) インターフェイスを使用してこのインターフェイスを取得する [QueryInterface](/visual-cpp/atl/queryinterface)です。  
  
## Vtable 順序のメソッド  
 によって提供されるメソッドに加え、 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) インターフェイス、このインターフェイスは、次を実装します。  
  
|メソッド|説明|  
|----------|--------|  
|[GetMemoryObject](../../../extensibility/debugger/reference/idebugbinder3-getmemoryobject.md)|このオブジェクトがバインドされているメモリを表すメモリ オブジェクトを取得します。|  
|[GetExceptionObjectAndType](../../../extensibility/debugger/reference/idebugbinder3-getexceptionobjectandtype.md)|\(もしあれば\) このオブジェクトに関連付けられている例外を取得します。|  
|[FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)|指定した名前、エイリアスを取得します。|  
|[GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)|このオブジェクトのすべてのエイリアスの配列を取得します。|  
|[GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md)|このオブジェクトに関連付けられている引数の型の数を取得します。|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)|このオブジェクトに関連付けられている引数の型の一覧を取得します。|  
|[GetEEService](../../../extensibility/debugger/reference/idebugbinder3-geteeservice.md)|ビジュアライザー サービスへのインターフェイスを取得します。|  
|[GetMemoryContext64](../../../extensibility/debugger/reference/idebugbinder3-getmemorycontext64.md)|メモリ コンテキスト オブジェクトの場所または 64 ビットのメモリ アドレスのいずれかに変換します。|  
  
## 必要条件  
 ヘッダー: ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [式評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)