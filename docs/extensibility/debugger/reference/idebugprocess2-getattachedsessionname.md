---
title: IDebugProcess2::GetAttachedSessionName |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4607026040bb790e34bf39fcd2b9cdf911251c81
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962822"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
このプロセスがデバッグ セッションの名前を取得します。 IDE では、特定のコンピューターの特定のプロセスのデバッグは、ユーザーにこの情報を表示できます。  
  
> [!NOTE]
>  このメソッドは廃止され、その実装を常に返します`E_NOTIMPL`します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstrSessionName`  
  
## <a name="return-value"></a>戻り値  
 このメソッドは常に返します`E_NOTIMPL`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)