---
title: "型のビジュアライザーおよびカスタム ビューアーを実装します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグ SDK] カスタム ビューアーのデバッグ"
  - "[デバッグ SDK] 型のビジュアライザーのデバッグ"
ms.assetid: abef18c0-8272-4451-b82a-b4624edaba7d
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 型のビジュアライザーおよびカスタム ビューアーを実装します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  Visual Studio 2015 では、式エバリュエーターを実装するには、この方法は推奨されません。 CLR 式エバリュエーターの実装については、次を参照してください [CLR 式エバリュエーター](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) と [マネージ式エバリュエーターのサンプル](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)します。  
  
 型のビジュアライザーとカスタム ビューアーは、数値の単純な 16 進数のダンプよりもわかりやすい方法で特定の種類のデータを表示するユーザーを許可します。 式エバリュエーター \(EE\) では、特定の型がデータまたは変数のカスタム ビューアーを関連付けることができます。 これらのカスタム ビューアーは、EE によって実装されます。 EE は、外部型のビジュアライザーを他のサード パーティ ベンダーまたはエンド ユーザーでも役に立つもサポートできます。  
  
## 説明  
  
### 型のビジュアライザー  
 Visual Studio では、\[ウォッチ\] ウィンドウに表示するには、型のビジュアライザーとすべてのオブジェクトに対してカスタム ビューアーの一覧を要求します。 式エバリュエーター \(EE\) では、このような型のビジュアライザーとカスタム ビューアーをサポートするか、すべての型の一覧が用意されています。 呼び出す [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) と [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 型ビジュアライザーとカスタム ビューアーにアクセスするためのプロセス全体を開始 \(を参照してください [視覚化して、データを表示します。](../../extensibility/debugger/visualizing-and-viewing-data.md) 呼び出しの順序の詳細\)。  
  
### カスタム ビューアー  
 カスタム ビューアーが特定のデータ型の EE で実装され、によって表される、 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) インターフェイスです。 その特定のカスタム ビューアーを実装する EE を実行する場合にのみ使用可能なために、カスタム ビューアーは型のビジュアライザーでは、ほど柔軟ではありません。 カスタム ビューアーを実装するは型のビジュアライザーのサポートを実装するよりも簡単です。 ただし、型のビジュアライザーをサポートするうえで最大限の柔軟性、エンドユーザーに自分のデータを視覚化します。 この説明の残りの部分では、型のビジュアライザーだけに関するものです。  
  
## インターフェイス  
 EE は、型のビジュアライザーを Visual Studio での使用をサポートするために、次のインターフェイスを実装します。  
  
-   [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)  
  
-   [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)  
  
-   [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)  
  
-   [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)  
  
-   [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)  
  
-   [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)  
  
 EE は、型のビジュアライザーをサポートするために次のインターフェイスを使用します。  
  
-   [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)  
  
-   [IEEVisualizerServiceProvider](../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)  
  
-   [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)  
  
## 参照  
 [CLR 式エバリュエーターの書き込み](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [視覚化して、データを表示します。](../../extensibility/debugger/visualizing-and-viewing-data.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)