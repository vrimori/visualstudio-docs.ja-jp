---
title: "BREAKREASON 列挙型 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: BREAKREASON
apilocation: scrobj.dll
helpviewer_keywords: BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf1baa8b627df50db33cbd86302ce06e80c1cf34
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="breakreason-enumeration"></a>BREAKREASON 列挙型
中断の原因を示します。  
  
## <a name="syntax"></a>構文  
  
```  
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
|BREAKREASON_STEP|言語エンジンがステップ実行モードです。|  
|BREAKREASON_BREAKPOINT|言語エンジンには、明示的なブレークポイントが発生しました。|  
|BREAKREASON_DEBUGGER_BLOCK|言語エンジンには、別のスレッドでデバッガー ブロックが発生しました。|  
|BREAKREASON_HOST_INITIATED|ホストは、中断を要求します。|  
|BREAKREASON_LANGUAGE_INITIATED|言語エンジンは、中断を要求します。|  
|BREAKREASON_DEBUGGER_HALT|IDE、デバッガーは、中断を要求しました。|  
|BREAKREASON_ERROR|中断の原因の実行エラー。|  
|BREAKREASON_JIT|JIT デバッグ スタートアップによって発生します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)