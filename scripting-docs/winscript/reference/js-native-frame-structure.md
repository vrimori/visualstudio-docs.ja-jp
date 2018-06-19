---
title: JS_NATIVE_FRAME 構造体 |Microsoft ドキュメント
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
ms.openlocfilehash: c7e93041a6dec767cb3bb11382abfb562068c925
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24733842"
---
# <a name="jsnativeframe-structure"></a>JS_NATIVE_FRAME 構造体
スタック フレームを表します。  
  
## <a name="syntax"></a>構文  
  
```  
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
  
## <a name="remarks"></a>コメント  
 `JS_NATIVE_FRAME` 構造体は `IJsStackFrameEnumerator` で使用されます。  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)