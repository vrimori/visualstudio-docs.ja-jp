---
title: "IActiveScript::SetScriptState | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptState
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptState"
ms.assetid: f2b2700c-0c8d-40db-ad84-dc751c5d9bc2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::SetScriptState
特定の状態にスクリプト エンジンを入力します。  このメソッドは、ベースの呼び出しによりオブジェクトをホストするまたは [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) のインターフェイスに非ベースのスレッドから外部に呼び出すことができます。  
  
## 構文  
  
```  
HRESULT SetScriptState(  
    SCRIPTSTATE ss  // identifier of new state  
);  
```  
  
#### パラメーター  
 `ss`  
 \[入力\]特定の状態にスクリプト エンジンを設定します。  [SCRIPTSTATE 列挙型](../../winscript/reference/scriptstate-enumeration.md) の列挙型で定義されている値の 1 つがあります。  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_FAIL`|スクリプト エンジンが初期化された状態への遷移をサポートしていません。  ホストは、このスクリプト エンジンを破棄し、新しいスクリプト エンジンを作成して初期化し、同じ効果を得るために読み込む必要があります。|  
|`E_UNEXPECTED`|呼び出し \(たとえば、スクリプト エンジンはまだ読み込まれていないか、初期化されず、および\) がありません。したがって失敗されていません。|  
|`OLESCRIPT_S_PENDING`|メソッドは正常に列を実行しましたが、状態は変更しません。  状態の変化が [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) のメソッドによって、サイトが呼び出されたとき。|  
|`S_FALSE`|メソッドが成功したスクリプトが特定の状態には既に存在していました。|  
  
## 解説  
 スクリプト エンジンの状態に関する詳細については、[Windows スクリプト エンジン](../../winscript/windows-script-engines.md) のスクリプト エンジンの状態のセクションを参照してください。  
  
## 参照  
 [IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)   
 [IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)   
 [IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)   
 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)