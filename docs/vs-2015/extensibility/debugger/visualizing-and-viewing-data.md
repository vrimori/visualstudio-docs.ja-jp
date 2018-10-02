---
title: 視覚化とデータの表示 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], viewing data
- debugging [Debugging SDK], visualizing data
ms.assetid: 699dd0f5-7569-40b3-ade6-d0fe53e832bc
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 10d83291a8d5820241ff2837b6b4a773c7b6fdba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47546677"
---
# <a name="visualizing-and-viewing-data"></a>データの視覚化と表示
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[視覚化してデータの表示](https://docs.microsoft.com/visualstudio/extensibility/debugger/visualizing-and-viewing-data)します。  
  
型のビジュアライザーおよびカスタム ビューアーが開発者にすぐにわかりやすい方法でデータを表示します。 式エバリュエーター (EE) できますサード パーティ製の型のビジュアライザーのサポートだけでなく、独自のカスタム ビューアーを指定します。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 指定数の型のビジュアライザーおよびカスタム ビューアーに関連付けられているオブジェクトの型を呼び出して、 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)メソッド。 Visual Studio を呼び出す場合は、少なくとも 1 つの型のビジュアライザーまたはカスタム ビューアー、 [GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)ビジュアライザーとビューアーがそれらの一覧を取得するメソッド (の一覧では実際には、`CLSID`を実装する、ビジュアライザーとビューアー)、ユーザーに提示します。  
  
## <a name="supporting-type-visualizers"></a>型のビジュアライザーのサポート  
 多くのインターフェイス型のビジュアライザーをサポートするために、EE を実装する必要があります。 これらのインターフェイスは 2 つのカテゴリに分類できます。 型のビジュアライザーとプロパティ データにアクセスするものを一覧表示されます。  
  
### <a name="listing-type-visualizers"></a>リスト型のビジュアライザー  
 EE のサポートの実装で型のビジュアライザーを一覧表示する`IDebugProperty3::GetCustomViewerCount`と`IDebugProperty3::GetCustomViewerList`します。 これらのメソッドは、対応するメソッドの呼び出しを渡す[GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)と[GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)します。  
  
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)を呼び出すことによって取得[CreateVisualizerService](../../extensibility/debugger/reference/ieevisualizerserviceprovider-createvisualizerservice.md)します。 このメソッドでは、 [IDebugBinder3](../../extensibility/debugger/reference/idebugbinder3.md)インターフェイスから取得される、 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md)に渡されたインターフェイス[EvaluateSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)します。 `IEEVisualizerServiceProvider::CreateVisualizerService` 必要です、 [IDebugSymbolProvider](../../extensibility/debugger/reference/idebugsymbolprovider.md)と[IDebugAddress](../../extensibility/debugger/reference/idebugaddress.md)インターフェイスに渡された`IDebugParsedExpression::EvaluateSync`します。 最終的なインターフェイスを作成するために必要な`IEEVisualizerService`インターフェイスは、 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) EE を実装するインターフェイス。 このインターフェイスには、ビジュアル化されているプロパティに対する変更ができます。 プロパティのすべてのデータにカプセル化、 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md)インターフェイスで、EE も実装されています。  
  
### <a name="accessing-property-data"></a>プロパティのデータにアクセスします。  
 プロパティのデータへのアクセスを行う、 [IPropertyProxyEESide](../../extensibility/debugger/reference/ipropertyproxyeeside.md)インターフェイス。 このインターフェイスを取得するには、Visual Studio を呼び出す[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)を取得するプロパティ オブジェクトの[IPropertyProxyProvider](../../extensibility/debugger/reference/ipropertyproxyprovider.md)インターフェイス (実装するのと同じオブジェクトに実装されている、 [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)インターフェイス) してから、 [GetPropertyProxy](../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)メソッドを取得する、`IPropertyProxyEESide`インターフェイス。  
  
 すべてのデータの入出力を渡された、`IPropertyProxyEESide`インターフェイスにカプセル化、 [IEEDataStorage](../../extensibility/debugger/reference/ieedatastorage.md)インターフェイス。 このインターフェイスは、バイトの配列を表しており、Visual Studio と EE の両方によって実装されます。 プロパティのデータを変更するかと、Visual Studio によって作成、`IEEDataStorage`呼び出し、新しいデータを保持しているオブジェクト[CreateReplacementObject](../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)新しいを取得するためには、そのデータ オブジェクトと`IEEDataStorage`オブジェクトですが、渡される[InPlaceUpdateObject](../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)プロパティのデータを更新します。 `IPropertyProxyEESide::CreateReplacementObject` により、実装する独自のクラスをインスタンス化する EE、`IEEDataStorage`インターフェイス。  
  
## <a name="supporting-custom-viewers"></a>カスタム ビューアーをサポートしています。  
 フラグ`DBG_ATTRIB_VALUE_CUSTOM_VIEWER`設定されている、`dwAttrib`のフィールド、 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md)構造 (への呼び出しによって返される[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)) をオブジェクトに関連付けられているカスタム ビューアーが含まれているかを示すられています。 このフラグを設定すると、Visual Studio を取得、 [IDebugProperty3](../../extensibility/debugger/reference/idebugproperty3.md)からインターフェイス、 [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)インターフェイスを使用して[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)します。  
  
 Visual Studio がビューアーのカスタム ビューアーをインスタンス化、ユーザーは、カスタム ビューアーを選択する場合`CLSID`によって提供される、`IDebugProperty3::GetCustomViewerList`メソッド。 Visual Studio を呼び出して[値](../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)をユーザーに値を表示します。  
  
 通常、`IDebugCustomViewer::DisplayValue`データの読み取り専用ビューを表示します。 データの変更を許可するのには、EE はプロパティ オブジェクトのデータの変更をサポートするカスタム インターフェイスを実装する必要があります。 `IDebugCustomViewer::DisplayValue`メソッドでは、このカスタム インターフェイスを使用して、データの変更をサポートします。 このメソッドは、カスタム インターフェイス、`IDebugProperty2`として渡されたインターフェイス、`pDebugProperty`引数。  
  
## <a name="supporting-both-type-visualizers-and-custom-viewers"></a>ビジュアライザーとカスタム ビューアーに入力両方をサポート  
 両方の型のビジュアライザーおよびカスタム ビューアー、EE をサポートできる、 [GetCustomViewerCount](../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)と[GetCustomViewerList](../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)メソッド。 によって返される値、EE がそれを提供しているカスタム ビューアーの数を追加する最初に、 [GetCustomViewerCount](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)メソッド。 EE の第 2 に、追加、`CLSID`によって返される一覧に、独自のカスタム ビューアーの s、 [GetCustomViewerList](../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [タスクのデバッグ](../../extensibility/debugger/debugging-tasks.md)   
 [型のビジュアライザーとカスタム ビューアー](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

