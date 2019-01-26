---
title: IEEDataStorage |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEEDataStorage
helpviewer_keywords:
- IEEDataStorage interface
ms.assetid: 704e932d-2325-410e-89c4-ce88c6ec19da
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bc409f455d93b84b12b9630a5f72f8e82a752d7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930973"
---
# <a name="ieedatastorage"></a>IEEDataStorage
このインターフェイスは、バイト配列を表します。  
  
## <a name="syntax"></a>構文  
  
```  
IEEDataStorage : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>実装についてのメモ  
 式エバリュエーター (EE) バイトの配列を表すためには、このインターフェイスを実装する (型のビジュアライザーを取得しを使用してデータを変更するために使用、 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)インターフェイス)。 EE は、通常、外部型のビジュアライザーをサポートするためには、このインターフェイスを実装します。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 メソッド、`IPropertyProxyEESide`すべてのインターフェイスは、このインターフェイスを返します。 呼び出す[GetPropertyProxy](../../../extensibility/debugger/reference/ipropertyproxyprovider-getpropertyproxy.md)を取得する、 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)インターフェイス。 呼び出す[QueryInterface](/cpp/atl/queryinterface)上、 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)を取得するインターフェイス、 [IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)インターフェイス。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序メソッド  
 `IEEDataStorage`インターフェイスは、次のメソッドを実装します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)|指定されたバッファーにデータの合計バイト数の指定を取得します。|  
|[GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)|使用できるデータのバイト数を取得します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスは、特定のオブジェクトによって保持されているデータにアクセスする型のビジュアライザーによって使用されます。 データは、型のビジュアライザーをユーザーに提示するときに必要な方法で操作できるように、バイト配列として扱われます。  
  
 カスタム ビューアーもこのインターフェイスを使用、必要な場合、カスタム ビューアーは、カスタムのインターフェイスを使用して一般的には、 [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)または[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md) (用文字列指向のデータの場合)。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [型のビジュアライザーとカスタム ビューアー](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)