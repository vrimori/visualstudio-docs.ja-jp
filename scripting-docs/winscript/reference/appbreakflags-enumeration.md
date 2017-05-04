---
title: "APPBREAKFLAGS 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: APPBREAKFLAGS
apilocation: scrobj.dll
helpviewer_keywords: 
  - "APPBREAKFLAGS 定数"
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# APPBREAKFLAGS 列挙型
アプリケーションおよびスレッドの現在のデバッグ状態を表示します。  
  
## 構文  
  
```cpp  
enum enum_APPBREAKFLAGS  
{  
APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,  
APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,  
APPBREAKFLAG_STEP= 0x00010000,  
APPBREAKFLAG_NESTED= 0x00020000,  
APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,  
APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,  
APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,  
APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,  
APPBREAKFLAG_IN_BREAKPOINT= 0x80000000  
};  
  
```  
  
## メンバー  
  
|メンバー|値|説明|  
|----------|-------|--------|  
|APPBREAKFLAG\_DEBUGGER\_BLOCK|0x00000001|言語のエンジンは BREAKREASON\_DEBUGGER\_BLOCK のすべてのスレッドで直ちに中断する必要があります。|  
|APPBREAKFLAG\_DEBUGGER\_HALT|0x00000002|言語のエンジンは BREAKREASON\_DEBUGGER\_HALT と直ちに中断する必要があります。|  
|APPBREAKFLAG\_STEP|0x00010000|言語のエンジンは BREAKREASON\_STEP の手順のスレッドで直ちに中断する必要があります。|  
|APPBREAKFLAG\_NESTED|0x00020000|アプリケーションは、ブレークポイントの入れ子になった実行にあります。|  
|APPBREAKFLAG\_STEPTYPE\_SOURCE|0x00000000|デバッガーは、ソース レベルでステップ実行されます。|  
|APPBREAKFLAG\_STEPTYPE\_BYTECODE|0x00100000|デバッガーは、バイト コード レベルでステップ実行されます。|  
|APPBREAKFLAG\_STEPTYPE\_MACHINE|0x00200000|デバッガーは、マシン レベルになっています。|  
|APPBREAKFLAG\_STEPTYPE\_MASK|0x00F00000|ステップの種類を検討するためのマスク。|  
|APPBREAKFLAG\_IN\_BREAKPOINT|0x80000000|ブレークポイントは進行中です。|  
  
## 解説  
 あるフラグは、他のフラグは、デバッガーのステップのモードを指定する言語がエンジンが次の機会を中断することを指定します。  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)   
 [BREAKREASON 列挙型](../../winscript/reference/breakreason-enumeration.md)