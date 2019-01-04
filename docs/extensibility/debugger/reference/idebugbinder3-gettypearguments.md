---
title: IDebugBinder3::GetTypeArguments |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetTypeArguments
helpviewer_keywords:
- IDebugBinder3::GetTypeArguments method
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c0151814261df2f57289edbb564e691b50c3acfd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987928"
---
# <a name="idebugbinder3gettypearguments"></a>IDebugBinder3::GetTypeArguments
このメソッドは、このオブジェクトに関連付けられている引数の型の一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```csharp  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `skip`  
 [in]引数の型を取得する前にスキップするフィールドの数。  
  
 `count`  
 [in]返される引数のフィールドの数 (ものサイズを指定します、`ppFields`配列)。  
  
 `ppFields`  
 [入力、出力]このメソッドの戻り値の入力フィールドの配列。  
  
 `pFetched`  
 [out]\(省略可能)引数の数は、実際に返されるフィールドを入力します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 引数の型の数を事前に取得できる[GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../../../extensibility/debugger/reference/idebugbinder3-gettypeargumentcount.md)