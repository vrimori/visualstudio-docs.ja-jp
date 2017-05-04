---
title: "BREAKREASON 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKREASON
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKREASON 列挙型"
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# BREAKREASON 列挙型
中断の原因となった操作、示します。  
  
## 構文  
  
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
  
## メンバー  
  
|メンバー|説明|  
|----------|--------|  
|BREAKREASON\_STEP|言語エンジンは、ステップのモードです。|  
|BREAKREASON\_BREAKPOINT|言語エンジンは、明示的なブレークポイントが発生しました。|  
|BREAKREASON\_DEBUGGER\_BLOCK|言語のエンジンは別のスレッドのデバッガーのブロックが発生しました。|  
|BREAKREASON\_HOST\_INITIATED|ホストは中断を要求しました。|  
|BREAKREASON\_LANGUAGE\_INITIATED|言語のエンジンは中断を要求しました。|  
|BREAKREASON\_DEBUGGER\_HALT|IDE では、デバッガーの中断を要求しました。|  
|BREAKREASON\_ERROR|実行発生したエラーによって中断が発生しました。|  
|BREAKREASON\_JIT|JIT デバッグの起動時によって引き起こされる。|  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)