---
title: IPropertyProxyEESide::CreateReplacementObject |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: be5433457ef533c1ef4dba66bf0b6d0d95546e3e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53959904"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
式エバリュエーター (EE) に固有のデータ オブジェクトのコピーを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateReplacementObject(  
   IEEDataStorage*  dataIn,  
   IEEDataStorage** dataOut  
);  
```  
  
```csharp  
int CreateReplacementObject(  
   IEEDataStorage     dataIn,  
   out IEEDataStorage dataOut  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dataIn`  
 [in][IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)データのコピーを保持しているオブジェクト。  
  
 `dataOut`  
 [out]新しいを返します`IEEDataStorage`オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが指定された、 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)バイトの配列を表すオブジェクト。 この入力方向のデータ オブジェクトは通常、EE によって実装されていません。 ただし、このメソッドによって返されるオブジェクトは、EE 実装できるように、EE によって実装は常に、`IEEDataStorage`でどのようなクラスが必要なインターフェイスです。  
  
 データが受信によって提供されることに注意してください。`IEEDataStorage`オブジェクトは、送信で同じデータである必要があります`IEEDataStorage`オブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)   
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)