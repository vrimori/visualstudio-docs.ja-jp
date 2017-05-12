---
title: "IJsDebugStackWalker インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 3fe30394-49c8-48e9-bde9-ffe5d79b2121
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugStackWalker インターフェイス
指定したスレッドのスタック ウォーカーを表します。  
  
## 構文  
  
```  
IJsDebugStackWalker : public IUnknown;  
```  
  
## メンバー  
  
### パブリック メソッド  
  
|Name|Description|  
|----------|-----------------|  
|[IJsDebugStackWalker::GetNext メソッド](../../winscript/reference/ijsdebugstackwalker-getnext-method.md)|Gets the next frame.|  
  
## 解説  
 スタック ウォーカーはターゲット プロセスの停止中にのみ作成でき、そのプロセスが再び続行されると無効になります。  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)