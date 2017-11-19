---
title: "IPropertyProxyEESide::InPlaceUpdateObject |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IPropertyProxyEESide::InPlaceUpdateObject
helpviewer_keywords: IPropertyProxyEESide::InPlaceUpdateObject
ms.assetid: abf89411-1853-4f23-b244-d5e0afa197b1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 723a24a0a0ce21c7817b5dfcef2680808f9319a0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ipropertyproxyeesideinplaceupdateobject"></a>IPropertyProxyEESide::InPlaceUpdateObject
指定されたデータ オブジェクトで、オブジェクトのデータを更新し、オブジェクトの新しいデータを表す新しいデータ オブジェクトを返します。  
  
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
 [in][IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)新しいデータを含むオブジェクト。  
  
 `dataOut`  
 [out]新しいを返します`IEEDataStorage`交換データを含むオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、実際には、オブジェクトのデータを更新します。 返されたデータ[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)オブジェクトは、入力方向のデータと同じである必要はありません`IEEDataStorage`オブジェクトが返されたオブジェクトは、プロパティの現在の値を反映する必要があります。  
  
 入力方向のデータ オブジェクトは通常、EE によって実装されていません。 ただし、このメソッドによって返されるオブジェクトは常に実装して EE を実装できるようにすると、EE、`IEEDataStorage`にどのようなクラスが必要なインターフェイスです。  
  
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)メソッドは、入力方向のデータ オブジェクトに基づくデータ オブジェクトを作成しますが、プロパティの元のデータには影響しません。  
  
## <a name="see-also"></a>関連項目  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [CreateReplacementObject](../../../extensibility/debugger/reference/ipropertyproxyeeside-createreplacementobject.md)