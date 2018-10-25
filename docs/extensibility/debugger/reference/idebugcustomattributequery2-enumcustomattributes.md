---
title: IDebugCustomAttributeQuery2::EnumCustomAttributes |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 18342a7879458f7463ccf76baa17afd0d7f8be96
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855509"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
このフィールドにアタッチされているすべてのカスタム属性の列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumCustomAttributes(   
   IEnumDebugCustomAttributes** ppEnum  
);  
```  
  
```csharp  
int EnumCustomAttributes(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]返します、 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)をカスタム属性の一覧を表すオブジェクト。 それ以外の場合、カスタム属性がない場合に null 値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合は、S_OK または S_FALSE をこのフィールドにカスタム属性がない場合は、返します。 それ以外の場合、エラー コードでは; を返します  
  
## <a name="remarks"></a>Remarks  
 フィールドには、複数のカスタム属性を持つことができます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)