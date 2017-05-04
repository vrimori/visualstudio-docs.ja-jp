---
title: "IActiveScript::GetScriptThreadState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadState"
ms.assetid: 7cac94d0-436e-4c29-895b-0c4afa0b3ccc
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadState
スクリプトのスレッドの現在の状態を取得します。  
  
## 構文  
  
```  
HRESULT GetScriptThreadState(  
    SCRIPTTHREADID stidThread,    // identifier of script thread  
    SCRIPTTHREADSTATE *pstsState  // receives state flag  
);  
```  
  
#### パラメーター  
 `stidThread`  
 \[入力\]状態を有効にするスレッドの ID、または特別なスレッド識別子の 1 つが:  
  
|値|説明|  
|-------|--------|  
|SCRIPTTHREADID\_BASE|基本スレッド; つまり、スクリプト エンジンのインスタンスが作成されたスレッド。|  
|SCRIPTTHREADID\_CURRENT|現在実行中のスレッド。|  
  
 `pstsState`  
 \[出力\]指定したスレッドの状態を受け取る変数のアドレス。  状態は [SCRIPTTHREADSTATE 列挙型](../../winscript/reference/scriptthreadstate-enumeration.md) の列挙型で定義されている名前付き定数値の 1 によって示されます。  このパラメーターに現在のスレッドを識別する、状態はいつでも変更される場合があります。  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが想定されていません \(たとえば、スクリプト エンジンはまだ読み込まれていないか、初期化されていません\)。|  
  
## 解説  
 このメソッドは、ベースの呼び出しによりオブジェクトをホストするまたは [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) のインターフェイスに非ベースのスレッドから外部に呼び出すことができます。  
  
## 参照  
 [IActiveScript](../../winscript/reference/iactivescript.md)