---
title: "IDebugEngine2::SetLocale |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::SetLocale
helpviewer_keywords: IDebugEngine2::SetLocale
ms.assetid: cd0d2cf1-2aac-43da-a830-4bb3d696c219
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41ad173f706b655f4d43a101618127070ae9ac6e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2setlocale"></a>IDebugEngine2::SetLocale
デバッグ エンジン (DE) のロケールを設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetLocale(   
   WORD wLangID  
);  
```  
  
```csharp  
int SetLocale(   
   ushort wLangID  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `wLangID`  
 [in]言語ロケールを指定します。 たとえば、英語の場合は 1033 です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、セッション デバッグ マネージャー、DE によって返される文字列は正しくローカライズできるように、IDE のロケール設定を反映するには、(SDM) によって呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)