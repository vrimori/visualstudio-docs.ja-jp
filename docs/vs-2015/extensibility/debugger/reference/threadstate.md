---
title: THREADSTATE |Microsoft Docs
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
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 07c4fe23f4bef02282ba1d53f4953f41d1f6343e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814755"
---
# <a name="threadstate"></a>THREADSTATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

スレッドの状態を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```csharp  
public enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
```  
  
## <a name="members"></a>メンバー  
 THREADSTATE_RUNNING  
 スレッドが実行されていることを示します。  
  
 THREADSTATE_STOPPED  
 ブレークポイントのため、スレッドが停止していることを示します。  
  
 THREADSTATE_FRESH  
 スレッドが作成されたらは、コードがまだ実行されていないことを示します。  
  
 THREADSTATE_DEAD  
 スレッドが実行されないことを示します。  
  
 THREADSTATE_FROZEN  
 スレッドが固定されていることを示します (の実行を実行できません)。  
  
## <a name="remarks"></a>Remarks  
 使用、`dwThreadState`のフィールド、 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)構造体。  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)

