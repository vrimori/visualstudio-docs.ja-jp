---
title: IPropertyProxyEESide |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IPropertyProxyEESide
helpviewer_keywords:
- IPropertyProxyEESide interface
ms.assetid: cf227cf8-39d9-4758-8f7e-a697aebb1926
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a68acb7f7ea3e11805bd0396563afb6e4eeea11
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808402"
---
# <a name="ipropertyproxyeeside"></a>IPropertyProxyEESide
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このインターフェイスは、関連付けられたオブジェクトのデータを表示するメソッドを提供します。 このインターフェイスは、型のビジュアライザーのサポートの一部です。  
  
## <a name="syntax"></a>構文  
  
```  
IPropertyProxyEESide : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーターでは、型のビジュアライザーをサポートするためにこのインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 呼び出す[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)このインターフェイスを取得します。 呼び出す[QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3)上、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)を取得するインターフェイス、 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)インターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
 次のメソッドは、このインターフェイスによって実装されます。  
  
|メソッド|説明|  
|------------|-----------------|  
|[InitSourceDataProvider](../../../extensibility/debugger/reference/ipropertyproxyeeside-initsourcedataprovider.md)|オブジェクトのデータにアクセスできるように、データ ソースのプロバイダーを初期化します。|  
|[GetManagedViewerCreationData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getmanagedviewercreationdata.md)|オブジェクトのアセンブリに関する情報を取得します。|  
|[GetInitialData](../../../extensibility/debugger/reference/ipropertyproxyeeside-getinitialdata.md)|オブジェクトの最初のデータを取得します。|  
|[CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)|既存のデータ ストレージのコピーを作成します。|  
|[InPlaceUpdateObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-inplaceupdateobject.md)|既存のデータ記憶域への参照を作成します。|  
|[ResolveAssemblyRef](../../../extensibility/debugger/reference/ipropertyproxyeeside-resolveassemblyref.md)|このオブジェクトを含むアセンブリのコンテキストで特定のアセンブリに関する情報を取得します。|  
  
## <a name="remarks"></a>Remarks  
 型のビジュアライザーは、このインターフェイスの一部であるオブジェクトに関連付けられた値にアクセスするのにこのインターフェイスを使用します。 データをアクセス、 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)インターフェイスで、データの読み取り専用ビューを提供します。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

