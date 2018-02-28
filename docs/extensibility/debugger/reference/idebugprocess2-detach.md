---
title: "IDebugProcess2::Detach |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c308dae9b324871f8604b6bedecf3d297f3eacd2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
すべてのプロセスでプログラムをデタッチすることにより、このプロセスからデバッガーをデタッチします。  
  
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
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 すべてのプログラムおよびプロセスの実行は継続が、デバッグ セッションの一部ではなくなりました。 デタッチ後に、操作は、このプロセス (およびそのプログラム) イベントが送信される、完全な以上のデバッグがします。  
  
## <a name="see-also"></a>参照  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)