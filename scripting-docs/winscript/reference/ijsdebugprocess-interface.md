---
title: "IJsDebugProcess インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a7ad5525-55b7-4c68-a4f7-c508f7877712
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugProcess インターフェイス
ターゲット プロセスを検査および制御するためのルーチンを提供します。  
  
## 構文  
  
```  
IJsDebugProcess : public IUnknown;  
```  
  
## メンバー  
  
### パブリック メソッド  
  
|名前|説明|  
|--------|--------|  
|[IJsDebugProcess::CreateBreakPoint メソッド](../../winscript/reference/ijsdebugprocess-createbreakpoint-method.md)|指定されたドキュメントの位置にブレークポイントを設定します。|  
|[IJsDebugProcess::CreateStackWalker メソッド](../../winscript/reference/ijsdebugprocess-createstackwalker-method.md)|スタック ウォーカーのファクトリ メソッド。|  
|[IJsDebugProcess::PerformAsyncBreak メソッド](../../winscript/reference/ijsdebugprocess-performasyncbreak-method.md)|スクリプト エンジンを中断モードにして、次のスクリプト命令で中断させます。|  
  
## 必要条件  
 **ヘッダー:** jscript9diag.h  
  
## 参照  
 [Windows スクリプト インターフェイスのリファレンス](../../winscript/reference/windows-script-interfaces-reference.md)