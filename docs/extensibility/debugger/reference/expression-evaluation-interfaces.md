---
title: "式評価インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "式の評価、インターフェイス"
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 式評価インターフェイス
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 式の評価のインターフェイスは、次のとおり、 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Debugging SDK。  
  
## 説明  
 これらのインターフェイスを使用して、中断モードで呼び出し履歴内の式を評価します。 共通言語ランタイムの式エバリュエーター \(EE\) に対してのみ実装されます。  
  
 テーブル内の各インターフェイスは、次の一覧から実装するコンポーネントを示しています。  
  
-   デバッグ エンジン \(DE\)  
  
-   式エバリュエーター \(EE\)  
  
-   Visual Studio \(VS\)  
  
|インターフェイス|によって実装されます。|説明|  
|--------------|-----------------|--------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|変数の numeric の別名を表します。|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|変数の numeric エイリアスを表し、式エバリュエーター エイリアスのアプリケーション ドメインを取得するには、\(EE\) できるようにします。|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|配列オブジェクトを表します。|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|マネージ配列オブジェクトを表すでき、式エバリュエーター、配列の基本のインデックス \(下限\) を確認するには、\(EE\) できます。|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|バインドのデバッグにメモリ内の実際のアドレスのシンボル バインダーを表します。|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|同じ、 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) インターフェイスが型、エイリアス、およびカスタムのビジュアライザーにアクセスを提供します。|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|式エバリュエーターを表します。|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|式エバリュエーター \(EE\) の拡張のバージョンを表します。|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|強化されたパーサー ツリーを使用して、式エバリュエーター \(EE\) を表します。|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|関数を表します。|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|関数を表し、強化、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) インターフェイスです。|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|デバッガーの出力ウィンドウにメッセージを表示する式エバリュエーター \(EE\) を有効にします。|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|マネージ コード オブジェクトを表します。|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|任意の記号を表す基本インターフェイスは、メモリ アドレスにバインドされます。|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|同じ、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) インターフェイスが追加情報へのアクセスを提供します。|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|評価する準備が解析された式を表します。|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|ポインターを表します。|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|解析ツリー内のポインターを表し、拡張、 **IDebugPointerObject** インターフェイスです。|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|型のビジュアライザーを型の値を変更する機能を提供します。|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|カスタム ビューアーとビジュアライザーの型へのアクセスを提供します。|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|作成する機能を提供する [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) オブジェクトです。|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) オブジェクトのコレクションを表します。|  
  
## 参照  
 [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [CLR 式エバリュエーターの書き込み](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)