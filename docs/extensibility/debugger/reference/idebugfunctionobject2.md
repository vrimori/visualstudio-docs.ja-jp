---
title: "IDebugFunctionObject2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2 インターフェイス"
ms.assetid: 56b2fdff-146d-4138-a34c-59a9c65a3ddd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 関数を表し、強化、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) インターフェイスです。  
  
## 構文  
  
```  
IDebugFunctionObject2 : IUnknown  
```  
  
## 実装についてのメモ  
 式エバリュエーター \(EE\) では、関数を表すためには、このインターフェイスを実装します。  
  
## 呼び出し元のノート  
 このインターフェイスのメソッドは遅延の **IDebugFunctionObject** 次のようにします。  
  
-   **IDebugEvaluate** メソッドはフラグを受け取ります。  
  
-   **CreateObject** メソッドはフラグとタイムアウトします。  
  
-   **CreateStringObjectWithLength** メソッドは、長さを受け取ります。  
  
## メソッド  
 このインターフェイスには、次のメソッドを実装します。  
  
|メソッド|説明|  
|----------|--------|  
|[CreateObject](../../../extensibility/debugger/reference/idebugfunctionobject2-createobject.md)|評価フラグの設定と、タイムアウト値が指定されたコンス トラクターを使用するオブジェクトを作成します。|  
|[CreateStringObjectWithLength](../../../extensibility/debugger/reference/idebugfunctionobject2-createstringobjectwithlength.md)|指定した長さを持つ文字列オブジェクトを作成します。|  
|[評価します。](../../../extensibility/debugger/reference/idebugfunctionobject2-evaluate.md)|関数の呼び出しをオブジェクトとして結果の値を返します。|  
  
## 必要条件  
 ヘッダー: Ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll