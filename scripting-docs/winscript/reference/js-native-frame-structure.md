---
title: "JS_NATIVE_FRAME 構造体 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_NATIVE_FRAME
apilocation: jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JS_NATIVE_FRAME 構造体
スタック フレームを表します。  
  
## 構文  
  
```  
typedef struct {  
    UINT64 InstructionOffset;  
    UINT64 ReturnOffset;  
    UINT64 FrameOffset;  
    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## メンバー  
 `InstructionOffset`  
 命令ポインター。  
  
 `ReturnOffset`  
 リターン アドレス。  
  
 `FrameOffset`  
 フレーム ポインター。  
  
 `StackOffset`  
 スタック ポインター。  
  
## 解説  
 `JS_NATIVE_FRAME` 構造体は `IJsStackFrameEnumerator` で使用されます。  
  
## 参照  
 [アクティブ スクリプト デバッガーの定数、列挙型、および構造体](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)