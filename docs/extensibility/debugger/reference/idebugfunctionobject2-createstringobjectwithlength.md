---
title: IDebugFunctionObject2::CreateStringObjectWithLength |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b43bf35b916616524c45847e378e1f63752cda1e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843883"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
指定した長さの文字列オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateStringObjectWithLength (  
   LPCOLESTR      pcstrString,  
   UINT           uiLength,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateStringObjectWithLength (  
   string           pcstrString,  
   uint             uiLength,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pcstrString`  
 [in]文字列オブジェクトの文字列値。  
  
 `uiLength`  
 [in]文字列のバイト単位の長さ。  
  
 `ppObject`  
 [out]返します、 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)新しく作成された文字列オブジェクトを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)