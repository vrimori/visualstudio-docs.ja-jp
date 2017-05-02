---
title: "JsDebugReadMemoryFlags 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsDebugReadMemoryFlags 列挙型
メモリの読み取り時の動作を指定するフラグ。  
  
## 構文  
  
```  
enum JsDebugReadMemoryFlags  
{  
   None = 0,  
   JsDebugAllowPartialRead= 0x1  
} JsDebugReadMemoryFlags;  
```  
  
## メンバー  
  
### 値  
  
|Name|Description|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|メモリの一部のみ正常に読み取られたときでも、呼び出し元で読み取り操作が正常に完了する必要がある場合に指定します。  このフラグを設定すると、"アドレス" が無効な場合のみ、E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS エラーが発生します。  このフラグを指定しない場合、要求したメモリのいずれかの部分を読み取れないと、E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS エラーが発生します。|  
|`None`|呼び出し元で ReadMemory の既定の動作が必要な場合に指定します。|  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)