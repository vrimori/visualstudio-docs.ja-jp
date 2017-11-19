---
title: "IDebugProcessEx2::Detach |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcessEx2::Detach
helpviewer_keywords: IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d810008391398741e644da7215de174918db604f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
このメソッドは、セッションが不要になった、プロセスをデバッグしているプロセスに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pSession`  
 [in]このプロセスからデタッチするセッションを一意に識別する値。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 渡されたインターフェイス`pSession`がクッキーとしてのみ扱われるは、このプロセスにアタッチされた最初のセッションのデバッグ マネージャーを一意に識別する値はありません。 指定されたインターフェイスのメソッドの機能です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)