---
title: "IDebugProgram3::ExecuteOnThread |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b75ee8c7b53e751f322ba41bc3f93e2542e192ef
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
デバッガーのプログラムを実行します。 どのスレッドで、ユーザーが表示プログラムを実行するときにデバッガーの情報を提供し、スレッドが返されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```csharp  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pThread`  
 [in][IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 これには、デバッガーが停止後に実行を再開できます 3 つの異なる方法があります。  
  
-   実行します。 は、前の手順をキャンセルしに、次のブレークポイントまで実行します。  
  
-   手順: は、いずれかの古い手順をキャンセルし、新しい手順が完了するまで実行します。  
  
-   続行: を再度実行し、いずれかの古い手順のアクティブなままにします。  
  
 渡されるスレッド`ExecuteOnThread`をキャンセルする手順を決定する場合に便利です。 実行している実行スレッドがわからない場合は、すべてのステップをキャンセルします。 スレッドの知識さえあれば、のみ、アクティブなスレッドでの手順をキャンセルする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [実行します。](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)