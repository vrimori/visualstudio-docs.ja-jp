---
title: IPropertyProxyEESide::InPlaceUpdateObject |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ed69657823ac5e3ae821304aa6ffdbee55f39a70
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847618"
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
指定されたデータ オブジェクトとオブジェクトのデータを更新し、オブジェクトの新しいデータを表す新しいデータ オブジェクトを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dataIn`  
 [in][IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)新しいデータを格納しているオブジェクト。  
  
 `dataOut`  
 [out]新しいを返します`IEEDataStorage`置換されたデータを格納しているオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、実際には、オブジェクトのデータを更新します。 返されるデータ[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)オブジェクトは、受信データと同じである必要はありません`IEEDataStorage`オブジェクトが返されるオブジェクトは、プロパティの現在の値を反映する必要があります。  
  
 入力方向のデータ オブジェクトは通常、EE によって実装されていません。 ただし、このメソッドによって返されるオブジェクトは、EE 実装できるように、EE によって実装は常に、`IEEDataStorage`でどのようなクラスが必要なインターフェイスです。  
  
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)メソッドは、受信データ オブジェクトに基づくデータ オブジェクトを作成しますが、プロパティの元のデータには影響しません。  
  
## <a name="see-also"></a>関連項目  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)