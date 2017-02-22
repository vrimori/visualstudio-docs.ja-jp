---
title: "視覚化して、データを表示します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[デバッグの SDK] のデバッグ、データを表示します。"
  - "[デバッグの SDK] のデバッグ、データを視覚化します。"
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# 視覚化して、データを表示します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ビジュアライザーを入力する場合はカスタム ビューアーに意味のある方法でデータを示します。  式エバリュエーターは \(EE\)サードパーティの型のビジュアライザーをサポートし独自のカスタム ビューアーを指定できます。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] はビジュアライザーの型とカスタム ビューアーがオブジェクト型と [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) のメソッドを呼び出して関連付けられているかを判定します。  少なくとも 1 種類のビジュアライザーまたはカスタム ビューアーを使用できない場合Visual Studio はビジュアライザーやビューアーのリストを取得する [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) のメソッドを \(実際には `CLSID`のリストビジュアライザーとビューアーを実行する\) としユーザーに示します。  
  
## ビジュアライザーのサポート型  
 型のビジュアライザーをサポートするために実装する EE があるいくつかのインターフェイスを持ちます。  これらのインターフェイスは2 種類のカテゴリ分割することがあります : ビジュアライザーは型の一覧とプロパティ データがアクセスできる必要があります。  
  
### 型のビジュアライザーを示します。  
 EE は `IDebugProperty3::GetCustomViewerCount` と `IDebugProperty3::GetCustomViewerList` の実装の型のビジュアライザーの一覧をサポートします。  これらのメソッドは対応するメソッド [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) と [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) の呼び出しを渡します。  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) は [CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md) を呼び出すことになります。  このメソッドは [EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) に渡される [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) のインターフェイスから派生 [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md) のインターフェイスが必要です。  `IEEVisualizerServiceProvider::CreateVisualizerService` は`IDebugParsedExpression::EvaluateSync` に渡された [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md) と [IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md) のインターフェイスが必要です。  `IEEVisualizerService` のインターフェイスを作成するために必要な最終的なインターフェイスが EE を実行する [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) のインターフェイスです。  このインターフェイスは変更が表示されるプロパティに対して行われるようにします。  すべてのプロパティ データはEE によって実装されるインターフェイス [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) の内にカプセル化されます。  
  
### プロパティをデータ アクセス  
 プロパティ データにアクセス [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md) のインターフェイスを通じてされます。  [IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md) インターフェイス \(同じオブジェクトに実装 [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) のインターフェイス実装される\) 取得するにはこのインターフェイスを取得するにはプロパティ オブジェクトの Visual Studio では [QueryInterface](/visual-cpp/atl/queryinterface) しを `IPropertyProxyEESide` のインターフェイスを取得するために [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md) のメソッドを呼び出します。  
  
 `IPropertyProxyEESide` のインターフェイスおよびから渡されたすべてのデータが [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md) のインターフェイスにカプセル化されます。  このインターフェイスはバイト配列を表しVisual Studio および EE の両方で実行されます。  プロパティのデータが変更されるとVisual Studio によって新しいデータを保持 `IEEDataStorage` のオブジェクトを作成しそのプロパティのデータを更新するために[InPlaceUpdateObject](../Topic/IPropertyProxyEESide::InPlaceUpdateObject.md) に渡される `IEEDataStorage` の新しいオブジェクトを取得するにはデータ オブジェクトで [CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md) を呼び出します。  `IPropertyProxyEESide::CreateReplacementObject` は EE が `IEEDataStorage` のインターフェイスを実装する独自のクラスをインスタンス化することができます。  
  
## カスタム ビューアーのサポート  
 フラグ `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` はオブジェクトに関連付けられているカスタム ビューアーがあることを示す [DEBUG\_PROPERTY\_INFO](../../extensibility/debugger/reference/debug-property-info.md) の構造体の `dwAttrib` のフィールド セット \([GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) の呼び出しによって返される\) です。  このフラグが設定されている場合Visual Studio は [QueryInterface](/visual-cpp/atl/queryinterface) を使用して [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) のインターフェイスから [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md) インターフェイスを取得します。  
  
 ユーザーがカスタム ビューアーを選択するとVisual Studio は `IDebugProperty3::GetCustomViewerList` のメソッドで提示される `CLSID` ビューアーを使用してカスタム ビューアーをインスタンス化します。  Visual Studio によってユーザーが値を表示する [値](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) を呼び出します。  
  
 通常`IDebugCustomViewer::DisplayValue` はデータの読み取り専用ビューを示しています。  データの変更を許可するにはEE オブジェクトのプロパティはデータの変更カスタム インターフェイスを実装する必要があります。  `IDebugCustomViewer::DisplayValue` のメソッドはデータの変更をサポートするためこのカスタム インターフェイスを使用します。  メソッドは `pDebugProperty` の引数として渡された `IDebugProperty2` インターフェイスのカスタム インターフェイスを検索します。  
  
## 型の両方をサポートするビジュアライザーやカスタム ビューアー  
 EE は [GetCustomViewerCount](../Topic/IDebugProperty3::GetCustomViewerCount.md) と [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) のメソッドの型の両方とカスタム ビジュアライザー ビューアーをサポートできます。  まずEE は[GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) のメソッドによって返される値を指定するカスタム ビューアーの数値を加算します。  第 2 にEE は [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) のメソッドによって返されるリストに独自のカスタム ビューアー `CLSID`を追加します。  
  
## 参照  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)   
 [型のビジュアライザーとカスタム ビューアー](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)