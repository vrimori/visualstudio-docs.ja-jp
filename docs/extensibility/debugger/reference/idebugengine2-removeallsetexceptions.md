---
title: "IDebugEngine2::RemoveAllSetExceptions |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords: IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c4a70cf4d0f77ab86bbb919dfcdc40a8ad59dd0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
IDE が特定のランタイム アーキテクチャまたは言語の設定で例外の一覧を削除します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `guidType`  
 [in]言語の GUID またはデバッグ エンジンは実行時のアーキテクチャに固有の guid を指定します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドによって削除された例外は、以前の呼び出しによって設定された、 [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)メソッドです。  
  
 削除する特定の例外を呼び出し、 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)