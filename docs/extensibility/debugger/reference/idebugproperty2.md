---
title: "IDebugProperty2 | Microsoft Docs"
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
  - "IDebugProperty2"
helpviewer_keywords: 
  - "IDebugProperty2 インターフェイス"
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスにはスタック フレームのプロパティプログラムのドキュメント プロパティまたはそのほかのプロパティを表します。  プロパティは通常式の評価結果があります。  
  
> [!NOTE]
>  「プロパティ」をこのように使用するとその `IDebugProperty2` がこのようなエンティティをできますがクラスのメンバー変数混同しないようにしてください。  
  
## 構文  
  
```  
IDebugProperty2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements 値の特定の型を表すインターフェイス。この  たとえば値が式の評価メモリの表示に使用されるメモリのコンテキストまたは登録の一覧と値の結果として数値を使用できます。  
  
## 呼び出し元のメモ  
 評価の結果を表すこのインターフェイスを取得するに [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) または [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) を呼び出します。  `IDebugExpression2::EvaluateAsync` はプロパティを取得するために[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) を呼び出す [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) SDM へのインターフェイスを送信することでこのインターフェイスを返します。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) は関連付けられたスクリプト ドキュメントを作成するにはこのインターフェイスを返します。  
  
 [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) は関数の戻り値を表すためにこのインターフェイスを返します。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) は名前やメモリのコンテキストなどプログラムのさまざまなプロパティを表すためこのインターフェイスを返します。  
  
 [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) はローカル変数などのスタック フレームのさまざまなプロパティを表すためこのインターフェイスを返します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugProperty2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|プロパティを説明する [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) の構造体に格納します。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|文字列のプロパティの値を設定します。|  
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|指定された参照の値からプロパティの値を設定します。|  
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|プロパティの子を列挙します。|  
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|プロパティの親を返します。|  
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|プロパティは最派生のプロパティを定義するプロパティを返します。|  
|[GetMemoryBytes](../Topic/IDebugProperty2::GetMemoryBytes.md)|プロパティの値を構成するメモリのバイト数を返します。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|プロパティ値のメモリのコンテキストを返します。|  
|[GetSize](../Topic/IDebugProperty2::GetSize.md)|サイズはプロパティ値のサイズをバイト単位で返します。|  
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|この属性値への参照を返します。|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|プロパティの拡張情報を返します。|  
  
## 解説  
 `IDebugProperty2` のインターフェイスで表されるようにプロパティは名前型およびアドレスでの値として考えることができます。  一般用語では`IDebugProperty2` は親と子ノードと階層構造を持つものが表すことができます。  
  
 プロパティは通常移り変わり間だけ現在のスタック フレーム \(たとえば保持されます。  一方[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) のインターフェイスで表されるためには値がある限りメモリに保持されます。  
  
 IDE がユーザーが実行時にプロパティを表示および変更するために `IDebugProperty2` のインターフェイスを使用できます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)