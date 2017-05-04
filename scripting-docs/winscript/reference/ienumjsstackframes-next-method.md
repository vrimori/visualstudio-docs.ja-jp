---
title: "IEnumJsStackFrames::Next メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumJsStackFrames.Next
apilocation: jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumJsStackFrames::Next メソッド
Gets the specified number of frames.  
  
## 構文  
  
```  
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### パラメーター  
 `cFrameCount`  
 \[入力\] 取得するフレームの数。  
  
 `pFrames`  
 \[出力\] フレームを格納する配列。  
  
 `pcFetched`  
 \[出力\] 返されたフレーム数。  
  
## 戻り値  
  
## 必要条件  
 **Header:** jscript9diag.h  
  
## 参照  
 [IEnumJsStackFrames インターフェイス](../../winscript/reference/ienumjsstackframes-interface.md)