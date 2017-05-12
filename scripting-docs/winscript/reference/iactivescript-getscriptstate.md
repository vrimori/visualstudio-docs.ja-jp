---
title: "IActiveScript::GetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptState"
ms.assetid: 59837f7c-755d-45c4-8194-bd57638fe2e1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetScriptState
スクリプト エンジンの現在の状態を取得します。  このメソッドは、ベースの呼び出しによりオブジェクトをホストするまたは [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) のインターフェイスに非ベースのスレッドから外部に呼び出すことができます。  
  
## 構文  
  
```  
HRESULT GetScriptState(  
    SCRIPTSTATE *pss  // address of structure for state information  
);  
```  
  
#### パラメーター  
 `pss`  
 \[出力\]値を受け取る変数のアドレスは [SCRIPTSTATE 列挙型](../../winscript/reference/scriptstate-enumeration.md) の列挙型で定義されています。  値を呼び出し元のスレッドに関連付けられたスクリプト エンジンの現在の状態を示します。  
  
## 戻り値  
 無効なポインターが指定されている場合、または `E_POINTER` が成功した場合 `S_OK` 返します。  
  
## 参照  
 [IActiveScript](../../winscript/reference/iactivescript.md)