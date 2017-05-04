---
title: "IJsDebugStackWalker::GetNext メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugStackWalker.GetNext
apilocation: jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugStackWalker::GetNext メソッド
次のフレームを取得します。  
  
## 構文  
  
```  
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### パラメーター  
 `ppFrame`  
 \[出力\] スタック フレームを表すオブジェクト。  
  
## 戻り値  
  
## 解説  
 列挙するスタック フレームがなくなると E\_JsDEBUG\_OUTSIDE\_OF\_VM を返します。  
  
## 必要条件  
 **ヘッダー:** jscript9diag.h  
  
## 参照  
 [IJsDebugStackWalker インターフェイス](../../winscript/reference/ijsdebugstackwalker-interface.md)