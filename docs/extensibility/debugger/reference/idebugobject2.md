---
title: "IDebugObject2 | Microsoft Docs"
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
  - "IDebugObject2"
helpviewer_keywords: 
  - "IDebugObject2 インターフェイス"
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 このインターフェイスは、オブジェクトに関する追加情報を提供します。  
  
## 構文  
  
```  
IDebugObject2 : IDebugObject  
```  
  
## 実装についてのメモ  
 式エバリュエーターでは、エイリアスとオブジェクトに関する情報へのアクセスのサポートを提供するには、このインターフェイスを実装します。  
  
## 呼び出し元のノート  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) インターフェイスを使用してこのインターフェイスを取得できる [QueryInterface](/visual-cpp/atl/queryinterface)です。 また、 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) このインターフェイスを返します。  
  
## Vtable 順序のメソッド  
 上のメソッドだけでなく、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 、インターフェイス、 `IDebugObject2` インターフェイスは、次を実装します。  
  
|メソッド|説明|  
|----------|--------|  
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|フィールドまたは変数を取得 \(該当する場合\) をこのオブジェクトによって表されるプロパティをサポートすることがあります。|  
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|このオブジェクトの値を表すマネージ コード オブジェクトを取得します。|  
|[CreateAlias](../Topic/IDebugObject2::CreateAlias.md)|このオブジェクトの一意の ID を作成または既存のエイリアスを取得します。|  
|[GetAlias](../Topic/IDebugObject2::GetAlias.md)|存在する場合は、このオブジェクトに関連付けられているエイリアスを取得します。|  
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|このオブジェクトの型を取得します。|  
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|このオブジェクトがユーザー データを表すかどうかを決定します。|  
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|エディット コンティニュの状態が無効になっているかどうかを決定します。<br /><br /> カスタム式エバリュエーターは、このメソッドを実装していません \(常に返すことは `E_NOTIMPL`\)。|  
  
## 解説  
 参照してください [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) エイリアスについての議論します。  
  
## 必要条件  
 ヘッダー: ee.h  
  
 名前空間: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [式評価インターフェイス](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)