---
title: IDebugProcess2::CanDetach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21fc550482021397e219e685074a9cc9c6e6c837
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015577"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
セッション デバッグ マネージャー (SDM) が、プロセスをデタッチできるかどうかを決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK.`返します`S_FALSE`場合は、デバッガーがプロセスからデタッチできません。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)