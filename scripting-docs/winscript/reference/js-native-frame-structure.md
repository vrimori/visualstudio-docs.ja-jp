---
title: JS_NATIVE_FRAME 構造体 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_NATIVE_FRAME
apilocation:
- jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e408b9770c08139bc7c25779a64532ccec41caf8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090793"
---
# <a name="jsnativeframe-structure"></a>JS_NATIVE_FRAME 構造体
スタック フレームを表します。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef struct {  
    UINT64 InstructionOffset;    UINT64 ReturnOffset;    UINT64 FrameOffset;    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## <a name="members"></a>メンバー  
 `InstructionOffset`  
 命令ポインター。  
  
 `ReturnOffset`  
 リターン アドレス。  
  
 `FrameOffset`  
 フレーム ポインター。  
  
 `StackOffset`  
 スタック ポインター。  
  
## <a name="remarks"></a>Remarks  
 `JS_NATIVE_FRAME` 構造体は `IJsStackFrameEnumerator` で使用されます。  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)