---
title: IDebugField::GetInfo |Microsoft Docs
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
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8c5b3f3e2d2d33ef46dd6b523a662e687b98d1de
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202567"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドは、フィールドの表示可能な情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]組み合わせた[FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)定数を表示する情報を選択します。 フィールドが記号である場合は、これは通常記号名と型です。  
  
 `pFieldInfo`  
 [out]指定された情報を返します[FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)構造体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)

