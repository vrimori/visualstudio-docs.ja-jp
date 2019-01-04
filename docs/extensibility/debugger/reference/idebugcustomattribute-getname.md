---
title: IDebugCustomAttribute::GetName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 753964c19c27709af1adf7b38e92555a46559776
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53944698"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
カスタム属性の名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetName(   
   BSTR* bstrName  
);  
```  
  
```csharp  
int GetName(  
   out string bstrName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bstrName`  
 [out]カスタム属性の名前を含む文字列を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドによって返される名前付き属性を宣言するために使用するクラスの名前に対応します。 カスタム属性クラス自体の名前に対応して c# では、宣言で使用されるときにカスタム属性名から削除する"Attribute"というサフィックスとしてこの可能性がありますも一致しません。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)