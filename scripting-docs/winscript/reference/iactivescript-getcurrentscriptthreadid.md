---
title: "IActiveScript::GetCurrentScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetCurrentScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetCurrentScriptThreadID"
ms.assetid: b09e8b48-4209-480e-8b71-e99ee9ae2e17
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::GetCurrentScriptThreadID
現在実行しているスレッドのスクリプト エンジンを書き直して定義済み識別子を取得します。  識別子は [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) メソッドなどのスクリプトのスレッドで実行されたコントロールのメソッドの以降の呼び出しで使用できます。  
  
## 構文  
  
```  
HRESULT GetCurrentScriptThreadID(  
    SCRIPTTHREADID *pstidThread  // receives scripting thread identifier  
);  
```  
  
#### パラメーター  
 `pstidThread`  
 \[出力\]現在のスレッドに関連付けられたスクリプトのスレッド識別子を受け取る変数のアドレス。  この識別子の解釈は、スクリプト エンジンで行われます、Windows のスレッド識別子のコピーである場合があります。  Win32 スレッドが終了すると、この識別子は未割り当てのなり、別のスレッドに従って割り当てることができます。  
  
## 戻り値  
 無効なポインターが指定されている場合、または `E_POINTER` が成功した場合 `S_OK` 返します。  
  
## 解説  
 このメソッドは、ベースの呼び出しによりオブジェクトをホストするまたは [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) のインターフェイスに非ベースのスレッドから外部に呼び出すことができます。  
  
## 参照  
 [IActiveScript](../../winscript/reference/iactivescript.md)