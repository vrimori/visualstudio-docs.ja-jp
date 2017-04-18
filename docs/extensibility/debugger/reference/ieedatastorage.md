---
title: "IEEDataStorage |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 5ca58f2e8f192316f1359949242fbf523edcc032
ms.lasthandoff: 04/05/2017

---
# <a name="ieedatastorage"></a>IEEDataStorage
このインターフェイスは、バイト配列を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーター (EE) バイトの配列を表すためには、このインターフェイスを実装する (種類のビジュアライザーを取得しを使用してデータを変更するために使用、 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)インターフェイス)。 EE は、通常、外部型のビジュアライザーをサポートするためにこのインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 メソッド、`IPropertyProxyEESide`すべてのインターフェイスは、このインターフェイスを返します。 呼び出す[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)を取得する、 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)インターフェイスです。 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)を取得するインターフェイス、 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)インターフェイスです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 `IEEDataStorage`インターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|指定されたバッファーにデータのバイト数の指定した数を取得します。|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|使用できるデータのバイト数を取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、特定のオブジェクトによって保持されているデータにアクセスする型のビジュアライザーで使用します。 データは、任意の方法がユーザーに提示するために必要で操作する型のビジュアライザーを許可するバイト配列として扱われます。  
  
 カスタム ビューアーもこのインターフェイスを使用、必要な場合、カスタム ビューアーは、カスタムのインターフェイスを使用して一般的には、 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)または[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (用文字列指向のデータの場合)。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
