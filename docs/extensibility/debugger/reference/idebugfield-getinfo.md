---
title: "IDebugField::GetInfo |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetInfo
helpviewer_keywords: IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6ff061a73de70918480450ea8763f9eea2fc34cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
このメソッドは、フィールドの表示可能な情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetInfo(   
   FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO* pFieldInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_FIELD_INFO_FIELDS dwFields,  
   FIELD_INFO[] pFieldInfo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFields`  
 [in]組み合わせた[FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)を表示する情報を選択する定数。 フィールドを表す場合、シンボル、これは通常、シンボルの名前と種類です。  
  
 `pFieldInfo`  
 [out]提供された情報を返します[FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)構造体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)