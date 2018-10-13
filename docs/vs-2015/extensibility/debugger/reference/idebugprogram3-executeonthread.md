---
title: IDebugProgram3::ExecuteOnThread |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProgram3::ExecuteOnThread
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0c0fb0c76c24a787b04b673d016e223714de29d4
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212512"
---
# <a name="idebugprogram3executeonthread"></a>IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

デバッガーでプログラムを実行します。 プログラムを実行するときに表示するユーザー スレッドをデバッガーの情報を提供するスレッドが返されます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 デバッガーが停止後に実行を再開できる 3 つのさまざまな方法はあります。  
  
-   実行します。 は、前の手順をキャンセルし、これに、次のブレークポイントまで実行します。  
  
-   手順: はか前の手順をキャンセルし、新しい手順が完了するまで実行します。  
  
-   続行: を再度実行して、古いのいずれかの手順のアクティブなままにします。  
  
 渡されるスレッド`ExecuteOnThread`をキャンセルする手順を決定する場合に便利です。 実行している実行スレッドがわからない場合は、すべての手順をキャンセルします。 スレッドの知識があれば、のみのアクティブ スレッドで手順をキャンセルする必要があります。  
  
## <a name="see-also"></a>関連項目  
 [実行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)

