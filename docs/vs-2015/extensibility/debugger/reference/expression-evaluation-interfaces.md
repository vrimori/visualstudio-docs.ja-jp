---
title: 式の評価のインターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- expression evaluation, interfaces
ms.assetid: 2d259f60-2cd7-460e-b02d-24a8fb202850
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2362f0000ece6377a3dc2022e73afcc2fd024000
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262289"
---
# <a name="expression-evaluation-interfaces"></a>式の評価のインターフェイス
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細についてを参照してください[CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 次の式の評価のインターフェイス、 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] SDK のデバッグします。  
  
## <a name="discussion"></a>説明  
 これらのインターフェイスは、中断モード中に呼び出し履歴内の式を評価に使用されます。 共通言語ランタイム式エバリュエーター (EE) に対してのみ実装されます。  
  
 テーブル内の各インターフェイスは、次の一覧から実装するコンポーネントを示しています。  
  
-   デバッグ エンジン (DE)  
  
-   式エバリュエーター (EE)  
  
-   Visual Studio (VS)  
  
|Interface|によって実装されます。|説明|  
|---------------|--------------------|-----------------|  
|[IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)|EE|変数の数値のエイリアスを表します。|  
|[IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)|EE|数値のエイリアス、変数を表し、により、式エバリュエーター (EE) アプリケーション ドメインのエイリアスを取得します。|  
|[IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)|EE|配列オブジェクトを表します。|  
|[IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)|EE|マネージ配列オブジェクトを表し、でき、式エバリュエーター、配列のベース インデックス (下限) を確認するには、(EE)。|  
|[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)|DE|バインドがメモリ内の実際のアドレスにシンボルをデバッグするバインダーを表します。|  
|[IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)|DE|同じ、 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)インターフェイスは、型、エイリアス、およびカスタム ビジュアライザーをアクセスを提供します。|  
|[IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)|EE|式エバリュエーターを表します。|  
|[IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)|EE|式エバリュエーター (EE) の拡張のバージョンを表します。|  
|[IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)|EE|パーサーが強化されたツリーの式エバリュエーター (EE) を表します。|  
|[IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)|EE|関数を表します。|  
|[IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)|EE|関数を表し、強化、 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)インターフェイス。|  
|[IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)|DE|デバッガーの出力ウィンドウにメッセージを表示する式エバリュエーター (EE) を有効にします。|  
|[IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)|EE|マネージ コード オブジェクトを表します。|  
|[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)|EE|任意のシンボルを表す基本インターフェイスは、メモリ アドレスにバインドします。|  
|[IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)|EE|同じ、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)インターフェイスには、追加情報へのアクセスが用意されています。|  
|[IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)|EE|すぐに評価できる解析された式を表します。|  
|[IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)|EE|ポインターを表します。|  
|[IDebugPointerObject3](../../../extensibility/debugger/reference/idebugpointerobject3.md)|EE|解析ツリーでポインターを表し、拡張、 **IDebugPointerObject**インターフェイス。|  
|[IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)|EE|型のビジュアライザーで、型の値を変更できるようにをします。|  
|[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)|VS|カスタム ビューアーとビジュアライザーの型へのアクセスを提供します。|  
|[IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)|VS|作成する機能を提供する[IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)オブジェクト。|  
|[IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)|EE|コレクションを表します[IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)オブジェクト。|  
  
## <a name="see-also"></a>関連項目  
 [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [CLR の式エバリュエーターの書き込み](../../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

