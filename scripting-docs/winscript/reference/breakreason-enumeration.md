---
title: BREAKREASON 列挙型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5c0dc03d8d24014e28ecf9510fa3d5faa21dba2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096799"
---
# <a name="breakreason-enumeration"></a>BREAKREASON 列挙型
中断の原因を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|BREAKREASON_STEP|言語エンジンは、ステップ実行モードです。|  
|BREAKREASON_BREAKPOINT|言語エンジンには、明示的なブレークポイントが発生しました。|  
|BREAKREASON_DEBUGGER_BLOCK|言語エンジンには、別のスレッドでデバッガーのブロックが発生しました。|  
|BREAKREASON_HOST_INITIATED|ホストでは、中断を要求しました。|  
|BREAKREASON_LANGUAGE_INITIATED|言語エンジンでは、中断を要求しました。|  
|BREAKREASON_DEBUGGER_HALT|デバッガー IDE では、中断を要求しました。|  
|BREAKREASON_ERROR|実行エラーには、中断が発生します。|  
|BREAKREASON_JIT|JIT デバッグ スタートアップによって発生します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)