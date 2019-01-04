---
title: 型のビジュアライザーおよびカスタム ビューアーを実装する |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14e9efa179405602cd94fa7460a9c7790077403d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820453"
---
# <a name="implement-type-visualizers-and-custom-viewers"></a>型のビジュアライザーおよびカスタム ビューアーを実装します。
> [!IMPORTANT]
>  Visual Studio 2015 での式エバリュエーターの実装には、この方法は非推奨とされます。 CLR 式エバリュエーターの実装方法の詳細については、次を参照してください。 [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)と[マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。 
  
 型のビジュアライザーおよびカスタム ビューアーは、数値の単純な 16 進ダンプよりもわかりやすい方法で特定の種類のデータを表示するユーザーを使用できます。 式エバリュエーター (EE) は、カスタム ビューアーを特定の種類のデータまたは変数に関連付けることができます。 これらのカスタム ビューアーは、EE によって実装されます。 EE は、外部型のビジュアライザーは、別のサードパーティ ベンダーまたはでもエンドユーザーからもサポートできます。  
  
## <a name="discussion"></a>説明  
  
### <a name="type-visualizers"></a>型のビジュアライザー  
 Visual Studio では、ウォッチ ウィンドウに表示するには、型のビジュアライザーおよびカスタム ビューアーのすべてのオブジェクトの一覧を要求します。 式エバリュエーター (EE) は、このような型のビジュアライザーおよびカスタム ビューアーをサポートするか、すべての種類の一覧を提供します。 呼び出す[GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)と[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)型のビジュアライザーおよびカスタム ビューアーにアクセスするプロセス全体を開始 (を参照してください[視覚化してデータの表示](../../extensibility/debugger/visualizing-and-viewing-data.md)詳細については、呼び出し元のシーケンスで)。  
  
### <a name="custom-viewers"></a>カスタム ビューアー  
 カスタム ビューアーは特定のデータ型の EE で実装され、によって表されるが、 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)インターフェイス。 カスタム ビューアーはその特定のカスタム ビューアーを実装する EE を実行する場合にのみが利用できないために、型のビジュアライザーとしての柔軟性はありません。 カスタム ビューアーの実装は、型のビジュアライザーのサポートを実装するよりも簡単です。 ただし、型のビジュアライザーをサポートしている柔軟性が最大をユーザーがそのデータを視覚化するため。 この説明の残りの部分では、型のビジュアライザーのみに関するものです。  
  
## <a name="interfaces"></a>インターフェイス  
 EE は、Visual Studio で使用される、型のビジュアライザーをサポートするために、次のインターフェイスを実装します。  
  
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
- [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
- [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
- [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
- [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
- [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
  EE では、型のビジュアライザーをサポートするために、次のインターフェイスは使用します。  
  
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
- [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
- [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## <a name="see-also"></a>関連項目  
 [CLR の式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [視覚化とデータを表示します。](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)