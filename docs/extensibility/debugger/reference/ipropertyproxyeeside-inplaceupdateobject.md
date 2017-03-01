---
title: "IPropertyProxyEESide::InPlaceUpdateObject |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords:
- IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f07bc5831a0c25d4006005dd2c97af0ec111559a
ms.lasthandoff: 02/22/2017

---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
指定されたデータ オブジェクトとオブジェクトのデータを更新し、オブジェクトの新しいデータを表す新しいデータ オブジェクトを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT InPlaceUpdateObject(  
   [in] IEEDataStorage*   dataIn,  
   [out] IEEDataStorage** dataOut  
);  
```  
  
```c#  
int InPlaceUpdateObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dataIn`  
 [in][IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)新しいデータを格納するオブジェクト。  
  
 `dataOut`  
 [out]新しい返します`IEEDataStorage`置換されたデータを格納するオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返す`S_OK`。 そうしないと、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、実際には、オブジェクトのデータを更新します。 つまり、返されるデータ[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)オブジェクトは、受信した内のデータと同じである必要はありません`IEEDataStorage`オブジェクトが返されたオブジェクトは、プロパティの現在の値を反映する必要があります。  
  
 入力方向のデータ オブジェクトは通常、EE によって実装されていません。 ただし、このメソッドによって返されるオブジェクトは EE を実装できる EE によって実装されることは常に、`IEEDataStorage`にどのようなクラスが必要なインターフェイスです。  
  
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)メソッドは、受信データ オブジェクトに基づいてデータ オブジェクトを作成しますが、プロパティの元のデータには影響しません。  
  
## <a name="see-also"></a>関連項目  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)
