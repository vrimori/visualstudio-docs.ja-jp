---
title: IDebugProcessEx2::Attach |Microsoft Docs
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
- IDebugProcessEx2::Attach
helpviewer_keywords:
- IDebugProcessEx2::Attach method
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 118b86193d9241744d5faae3719ad53a593537f4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830538"
---
# <a name="idebugprocessex2attach"></a>IDebugProcessEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

このメソッドは、セッションがプロセスをデバッグして今すぐ、プロセスに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pSession`  
 [in]このプロセスにアタッチするセッションを一意に識別する値。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 インターフェイスが渡された`pSession`がクッキー、セッション デバッグ マネージャー; このプロセスにアタッチするを一意に識別する値としてのみ扱われる、指定されたインターフェイスのメソッドのいずれも機能します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)

