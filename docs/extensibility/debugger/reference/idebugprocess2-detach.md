---
title: IDebugProcess2::Detach |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 633ac46a70ffa7a6becfa0648b53e8f683f838b3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027806"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
すべてのプロセスでアプリケーションをデタッチすることにより、このプロセスからデバッガーをデタッチします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Detach(   
   void   
);  
```  
  
```csharp  
int Detach();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 すべてのプログラムおよびプロセスは、実行を継続が、デバッグ セッションの一部ではなくなりました。 デタッチ後操作は、このプロセス (およびそのプログラム) イベントが送信される、これ以上の完全なデバッグです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)