---
title: "BREAKPOINT_STATE 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: BREAKPOINT_STATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "BREAKPOINT_STATE 列挙型"
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# BREAKPOINT_STATE 列挙型
ブレークポイント条件を示します。  
  
## 構文  
  
```  
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## メンバー  
  
|メンバー|説明|  
|----------|--------|  
|BREAKPOINT\_DELETED|ブレークポイントはありませんが、それでも、それへの参照があります。|  
|BREAKPOINT\_DISABLED|ブレークポイントですが、は無効になります。|  
|BREAKPOINT\_ENABLED|ブレークポイントであり、が有効になります。|  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)