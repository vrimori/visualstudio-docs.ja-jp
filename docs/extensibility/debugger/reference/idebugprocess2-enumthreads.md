---
title: IDebugProcess2::EnumThreads |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c916e8b176444a8af81cb874c394e9eb832a01b4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49939710"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
プロセスで実行されているすべてのスレッドの一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumThreads(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```csharp  
int EnumThreads(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
 [out]返します、 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)プロセス内のすべてのプログラムのすべてのスレッドの一覧を格納しているオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、各プログラムで実行中のスレッドを列挙し、し、これらをスレッドのプロセス ビューに結合します。 複数のプログラムで実行される可能性が 1 つのスレッドこのメソッドは、そのスレッドを 1 回だけ列挙します。  
  
 このメソッドは、重複せず、プロセスのスレッドの一覧を表示します。 それ以外の場合、特定のプログラムで実行中のスレッドを列挙するために使用して、 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)