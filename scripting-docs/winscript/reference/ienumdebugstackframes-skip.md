---
title: "IEnumDebugStackFrames::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Skip
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Skip"
ms.assetid: d893d6e9-e119-4f14-99d0-bf23dbd2d625
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Skip
列挙体シーケンス内の指定した数のセグメントをスキップします。  
  
## 構文  
  
```  
HRESULT Skip(  
   ULONG  celt  
);  
```  
  
#### パラメーター  
 `celt`  
 \[スキップ\]列挙体シーケンス内の線分の数。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、列挙体シーケンスのセグメントの指定した数の要素をスキップします。  
  
## 参照  
 [IEnumDebugStackFrames インターフェイス](../../winscript/reference/ienumdebugstackframes-interface.md)