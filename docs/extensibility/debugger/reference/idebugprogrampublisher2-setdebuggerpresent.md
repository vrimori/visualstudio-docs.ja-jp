---
title: "IDebugProgramPublisher2::SetDebuggerPresent |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
helpviewer_keywords:
- IDebugProgramPublisher2::SetDebuggerPresent
ms.assetid: c88c3ff4-3632-4199-b5de-83c6d21bcf75
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 61ad9f9fe19de17d1dc21c4f9f9be24ffce2900a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogrampublisher2setdebuggerpresent"></a>IDebugProgramPublisher2::SetDebuggerPresent
デバッガーが存在し、実行されていることをプログラムの発行元に通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetDebuggerPresent(  
   BOOL fDebuggerPresent  
);  
```  
  
```csharp  
int SetDebuggerPresent(  
   int fDebuggerPresent  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `fDebuggerPresent`  
 [in]0 以外の値 (`TRUE`)、デバッガーが存在する場合は 0 (`FALSE`) されていない場合。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 デバッガーの有無から返されるデータに反映されますが、 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)メソッド: が返される値を設定または前回の呼び出しでは、オフ、`SetDebuggerPresent`メソッドです。  
  
## <a name="see-also"></a>参照  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [GetProviderProcessData](../../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md)