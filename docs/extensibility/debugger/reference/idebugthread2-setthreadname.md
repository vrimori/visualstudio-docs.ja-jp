---
title: IDebugThread2::SetThreadName |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::SetThreadName
helpviewer_keywords:
- IDebugThread2::SetThreadName
ms.assetid: fa934121-3f58-44dc-9c30-d3f752e44c8b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aae43ba6b9a7aa658a7c4e47afd0405ea15556eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31118191"
---
# <a name="idebugthread2setthreadname"></a>IDebugThread2::SetThreadName
スレッドの名前を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetThreadName (   
   LPCOLESTR pszName  
);  
```  
  
```csharp  
int SetThreadName (   
   string pszName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pszName`  
 [in]スレッドの名前。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 スレッド名を取得する、 [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [getName](../../../extensibility/debugger/reference/idebugthread2-getname.md)