---
title: "IDebugAlias | Microsoft Docs"
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
  - "IDebugAlias"
helpviewer_keywords: 
  - "IDebugAlias インターフェイス"
ms.assetid: 3cc4c9a4-7805-4239-b00e-eb4a024f3c55
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 変数の numeric の別名を表します。 エイリアスは、別の変数の名前だけです。  
  
## 構文  
  
```  
IDebugAlias : IUnknown  
```  
  
## 実装についてのメモ  
 式エバリュエーター \(EE\) では、変数の数値の別名をサポートするには、このインターフェイスを実装します。  
  
## 呼び出し元のノート  
 [CreateAlias](../Topic/IDebugObject2::CreateAlias.md) 特定のオブジェクトのエイリアスを作成します。 別名を使用して検索 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md) または [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)です。  
  
## Vtable 順序のメソッド  
 次の方法が定義されている、 `IDebugAlias` インターフェイスです。  
  
|メソッド|説明|  
|----------|--------|  
|[GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)|このエイリアスが参照するオブジェクトを取得します。|  
|[GetName](../../../extensibility/debugger/reference/idebugalias-getname.md)|エイリアス名を取得します。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugalias-geticordebugvalue.md)|取得、 `ICorDebugValue` へのアクセスを提供するインターフェイスがこのオブジェクト \(マネージ コードのみ\) については、コードを管理します。|  
|[破棄](../../../extensibility/debugger/reference/idebugalias-dispose.md)|エイリアスとしてもう使用されていないこのマークされます。|  
  
## 解説  
 エイリアスは、後に \# 文字、1001 \# などの文字列形式の 10 進数です。  
  
## 必要条件  
 ヘッダー: ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [式評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [CreateAlias](../Topic/IDebugObject2::CreateAlias.md)   
 [FindAlias](../../../extensibility/debugger/reference/idebugbinder3-findalias.md)   
 [GetAllAliases](../../../extensibility/debugger/reference/idebugbinder3-getallaliases.md)