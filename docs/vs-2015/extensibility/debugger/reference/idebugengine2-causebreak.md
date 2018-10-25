---
title: IDebugEngine2::CauseBreak |Microsoft Docs
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
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 29dc356f1964af5b1536760dc0f60dc9f5d3862d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923109"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

すべてのプログラムによってこのデバッグ エンジン (DE)、次回の実行を停止するデバッグ中の要求を実行すると、スレッドの 1 つ試行します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは非同期: [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)次に、プログラムはこのメソッドが呼び出された後に実行しようとしたときにイベントが送信されます。  
  
## <a name="see-also"></a>関連項目  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

