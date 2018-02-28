---
title: "IEnumDebugProcesses2::Skip |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugProcesses2::Skip
helpviewer_keywords:
- IEnumDebugProcesses2::Skip
ms.assetid: b9e9d888-189b-44c4-a65f-e91612458898
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: be1a34628fa6a7efae6c4d14f62ab2d265e7f428
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ienumdebugprocesses2skip"></a>IEnumDebugProcesses2::Skip
指定した要素数をスキップします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `celt`  
 [in]スキップする要素の数。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`場合`celt`残りの要素の数よりも大きいです。 それ以外の場合、エラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 場合`celt`数より大きい値を指定して残りの要素の列挙体が最後に設定し、`S_FALSE`が返されます。  
  
## <a name="see-also"></a>参照  
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)