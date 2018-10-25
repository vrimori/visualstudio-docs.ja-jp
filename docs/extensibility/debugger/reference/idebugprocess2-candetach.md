---
title: IDebugProcess2::CanDetach |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::CanDetach
helpviewer_keywords:
- IDebugProcess2::CanDetach
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 23a4ec112c33100a2eed8e4853f5a6280a741e12
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942141"
---
# <a name="idebugprocess2candetach"></a>IDebugProcess2::CanDetach
セッション デバッグ マネージャー (SDM) が、プロセスをデタッチできるかどうかを決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanDetach(  
   void  
);  
```  
  
```csharp  
int CanDetach();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK.`返します`S_FALSE`場合は、デバッガーがプロセスからデタッチできません。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)