---
title: THREADSTATE |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- THREADSTATE
helpviewer_keywords:
- THREADSTATE enumeration
ms.assetid: 62efdd7c-25b1-4fd3-9d06-ac1830a418a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8acfff2f3b37cfe44565a432ff150073b3ab07ba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962145"
---
# <a name="threadstate"></a>THREADSTATE
スレッドの状態を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
enum enum_THREADSTATE {   
   THREADSTATE_RUNNING = 0x0001,  
   THREADSTATE_STOPPED = 0x0002,  
   THREADSTATE_FRESH   = 0x0003,  
   THREADSTATE_DEAD    = 0x0004,  
   THREADSTATE_FROZEN  = 0x0005  
};  
typedef DWORD THREADSTATE;  
```  
  
```csharp  
public enum enum_THREADSTATE {   
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
  
 名前空間:Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ:Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [列挙型](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)