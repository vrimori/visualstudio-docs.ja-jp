---
title: 視覚化とデータの表示 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebaa07c8fe70e1842334b0bf7c28eb7491fd9c44
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="visualizing-and-viewing-data"></a>視覚化とデータを表示します。
ビジュアライザーの型とカスタム ビューアーを開発者に迅速にわかりやすい方法でデータを表示します。 式エバリュエーター (EE) サード パーティ製の種類のビジュアライザーをサポートしたりできるよう、独自のカスタム ビューアーを指定します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 決定数の種類のビジュアライザーとカスタム ビューアーに関連付けられたオブジェクトの型を呼び出して、 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)メソッドです。 Visual Studio の呼び出しがある場合に、少なくとも 1 つの型のビジュアライザーや、カスタム ビューアー使用可能な、 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)それらビジュアライザーとビューアーの一覧を取得する方法 (実際には、一連の`CLSID`s を実装する、ビジュアライザーとビューアー) をユーザーに提示します。  
  
## <a name="supporting-type-visualizers"></a>型のビジュアライザーをサポートします。  
 EE は、種類のビジュアライザーをサポートするために実装する必要がありますインターフェイスの数があります。 これらのインターフェイスを 2 つのカテゴリに細分化できます。 型ビジュアライザーとプロパティのデータにアクセスするものを一覧表示します。  
  
### <a name="listing-type-visualizers"></a>型のビジュアライザーの一覧  
 EE のサポートの実装の種類のビジュアライザーを一覧表示する`IDebugProperty3::GetCustomViewerCount`と`IDebugProperty3::GetCustomViewerList`です。 これらのメソッドは、対応するメソッドへの呼び出しを渡す[GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)と[GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)です。  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)呼び出すことによって取得[CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)です。 このメソッドが必要な[IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)インターフェイスから取得される、 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)に渡されたインターフェイス[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)です。 `IEEVisualizerServiceProvider::CreateVisualizerService` 必要です、 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)と[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)に渡されたインターフェイス`IDebugParsedExpression::EvaluateSync`です。 最終的なインターフェイスを作成するために必要な`IEEVisualizerService`インターフェイスは、 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) EE を実装するインターフェイスです。 このインターフェイスには、ビジュアル化されているプロパティに対する変更ができるようにします。 プロパティのすべてのデータにカプセル化されて、 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) EE によっても実装されるインターフェイス。  
  
### <a name="accessing-property-data"></a>プロパティのデータにアクセスします。  
 プロパティのデータへのアクセスは、操作には、 [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)インターフェイスです。 このインターフェイスを取得するには、Visual Studio を呼び出す[QueryInterface](/cpp/atl/queryinterface)取得するプロパティ オブジェクトを[IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)インターフェイス (を実装するのと同じオブジェクトに実装される、 [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)インターフェイス) してから呼び出して、 [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)を取得するメソッド、`IPropertyProxyEESide`インターフェイスです。  
  
 アウトや、すべてのデータが渡される、`IPropertyProxyEESide`にカプセル化するインターフェイス、 [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)インターフェイスです。 このインターフェイスは、バイトの配列を表します、Visual Studio と EE の両方で実装されます。 プロパティのデータを変更するかと、Visual Studio によって作成、`IEEDataStorage`呼び出し、新しいデータを保持するオブジェクト[CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)新しいを取得するためにそのデータ オブジェクト`IEEDataStorage`オブジェクトをさらには渡される[InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)プロパティのデータを更新します。 `IPropertyProxyEESide::CreateReplacementObject` 実装する独自のクラスをインスタンス化 EE は、`IEEDataStorage`インターフェイスです。  
  
## <a name="supporting-custom-viewers"></a>カスタム ビューアーをサポートします。  
 フラグ`DBG_ATTRIB_VALUE_CUSTOM_VIEWER`設定されている、`dwAttrib`のフィールド、 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)構造 (への呼び出しによって返される[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) を示す、オブジェクトに関連付けられているカスタム ビューアーが含まれています。関連付けします。 このフラグを設定すると、Visual Studio 取得、 [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)からインターフェイス、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)インターフェイスを使用して[QueryInterface](/cpp/atl/queryinterface)です。  
  
 Visual Studio が、ビューアーを使用して、カスタム ビューアーをインスタンス化ユーザーは、カスタム ビューアーを選択する場合`CLSID`によって提供される、`IDebugProperty3::GetCustomViewerList`メソッドです。 Visual Studio は、呼び出す[値](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)をユーザーに値を表示します。  
  
 通常、`IDebugCustomViewer::DisplayValue`データの読み取り専用ビューを表示します。 データへの変更を許可するのには、EE はプロパティ オブジェクトのデータの変更をサポートするカスタム インターフェイスを実装する必要があります。 `IDebugCustomViewer::DisplayValue`メソッドは、データの変更をサポートするためにこのカスタム インターフェイスを使用します。 カスタムのインターフェイス メソッドを検索、`IDebugProperty2`として渡されたインターフェイス、`pDebugProperty`引数。  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>ビジュアライザーとカスタム ビューアーに入力両方をサポートします。  
 EE は、ビジュアライザーの型とのカスタム ビューアーをサポートできます、 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)と[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)メソッドです。 EE がによって返される値、数の値を提供するカスタム ビューアーを追加する最初に、 [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)メソッドです。 EE を次に、追加、`CLSID`によって返される一覧に、独自のカスタム ビューアーの s、 [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)   
 [型のビジュアライザーとカスタム ビューアー](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)