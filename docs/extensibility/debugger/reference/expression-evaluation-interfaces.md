---
title: 式の評価インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be9582f965fe1d8a00c97548dbc5f458ae4e1198
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107401"
---
# <a name="expression-evaluation-interfaces"></a>式の評価インターフェイス
> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されなくなりました。 CLR 式エバリュエーターを実装する方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)です。  
  
 式の評価のインターフェイスは、次のとおり、 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] SDK のデバッグします。  
  
## <a name="discussion"></a>説明  
 これらのインターフェイスは、中断モード中に呼び出し履歴内の式を評価に使用されます。 これらは、共通言語ランタイムの式エバリュエーター (EE) に対してのみ実装されます。  
  
 テーブル内の各インターフェイスは、次の一覧からそれを実装できるコンポーネントを示しています。  
  
-   デバッグ エンジン (DE)  
  
-   式エバリュエーター (EE)  
  
-   Visual Studio (VS)  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|変数の数値のエイリアスを表します。|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|変数に対して数値のエイリアスを表し、式エバリュエーターの別名をアプリケーション ドメインを取得するには、(EE) できるようにします。|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|配列オブジェクトを表します。|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|マネージ配列オブジェクトを表すでき、式エバリュエーター (EE) 配列の基本のインデックス (下限) を確認できます。|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|バインドがメモリ内の実際のアドレスにシンボルをデバッグするバインダーを表します。|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|同じ、 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)インターフェイスは、型、エイリアス、およびカスタム ビジュアライザーをアクセスを提供します。|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|式エバリュエーターを表します。|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|式エバリュエーター (EE) の拡張のバージョンを表します。|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|強化されたパーサー ツリー式エバリュエーター (EE) を表します。|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|関数を表します。|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|関数を表し、強化、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)インターフェイスです。|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|デバッガーの出力 ウィンドウにメッセージを表示する式エバリュエーター (EE) を有効にします。|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|マネージ コード オブジェクトを表します。|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|任意の記号を表す基本インターフェイスは、メモリ アドレスにバインドします。|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|同じ、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)インターフェイスが追加情報へのアクセスを提供します。|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|評価する準備が解析された式を表します。|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|ポインターを表します。|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|解析ツリーでポインターを表し、拡張、 **IDebugPointerObject**インターフェイスです。|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|型のビジュアライザーで、型の値を変更する機能を提供します。|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|カスタム ビューアーとビジュアライザーの型へのアクセスを提供します。|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|作成する機能を提供する[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)オブジェクト。|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|コレクションを表します[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)オブジェクト。|  
  
## <a name="see-also"></a>関連項目  
 [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [CLR 式エバリュエーターの書き込み](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)