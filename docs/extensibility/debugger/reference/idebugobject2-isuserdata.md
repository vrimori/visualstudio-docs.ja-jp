---
title: IDebugObject2::IsUserData |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8c20b4e531284156b8790b1ca65b32c85d1db997
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31112286"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
オブジェクトがユーザー データを表すかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pfUser`  
 [out]0 以外を返します (`TRUE`) オブジェクトは、ユーザー データを表す場合は 0 (`FALSE`) しない場合。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 ユーザー データは、JustMyCode (そのため、スタック トレースに表示し、ユーザー コードとしてモジュールをマークするユーザー構成可能なオプション) として指定されたモジュールの一部である任意のオブジェクトです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)