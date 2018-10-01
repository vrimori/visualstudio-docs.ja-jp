---
title: IDebugObject2::GetField |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject2::GetField
helpviewer_keywords:
- IDebugObject2::GetField method
ms.assetid: add6a6b5-e752-47dd-9613-29206ea809b0
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ffa4577fe79078116759c789ee73904ad4ddc04f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548530"
---
# <a name="idebugobject2getfield"></a>IDebugObject2::GetField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDebugObject2::GetField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugobject2-getfield)します。  
  
このオブジェクトの型を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetField(  
 IDebugField** ppField  
);  
```  
  
```csharp  
int GetField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppField`  
 [out]返します、 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) null 値でない場合にオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 フィールドには、オブジェクトの型について説明します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

