---
title: "IDebugProperty2::GetParent |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty2::GetParent
helpviewer_keywords:
- IDebugProperty2::GetParent
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 3f33bf6fc0f7a93ed50f73766a9ed144bb0b9d8e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty2getparent"></a>IDebugProperty2::GetParent
プロパティの親プロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetParent (   
   IDebugProperty2** ppParent  
);  
```  
  
```csharp  
int GetParent (   
   out IDebugProperty2 ppParent  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppParent`  
 [out]返します、 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)プロパティの親を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`; エラー コードを返しますそれ以外の場合。 返します`S_GETPARENT_NO_PARENT`親が存在しない場合。  
  
## <a name="see-also"></a>参照  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)