---
title: "IActiveScript::GetScriptThreadID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptThreadID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptThreadID"
ms.assetid: 2595d76e-30b5-429f-88b4-1d026645dd9b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::GetScriptThreadID
特定の Win32 スレッドに関連付けられたスレッドのスクリプト エンジンを書き直して定義済み識別子を取得します。  
  
## 構文  
  
```  
HRESULT GetScriptThreadID(  
    DWORD dwWin32ThreadID,       // Win32 thread identifier.  
    SCRIPTTHREADID *pstidThread  // Receives scripting thread. identifier  
);  
```  
  
#### パラメーター  
 `dwWin32ThreadID` ,  
 \[出力\]現在実行中のプロセスの Win32 スレッドのスレッド識別子。  現在実行中のスレッドのスレッド識別子を取得するに [IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md) 関数を使用します。  
  
 `pstidThread` ,  
 \[入力\]特定の Win32 スレッドに関連付けられたスクリプトのスレッド識別子を受け取る変数のアドレス。  この識別子の解釈は、スクリプト エンジンで行われます、Windows のスレッド識別子のコピーである場合があります。  Win32 スレッドが終了すると、この識別子は未割り当てのなり、別のスレッドに従って割り当てられた可能性があることに注意してください。  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出し \(たとえば、スクリプト エンジンはまだ読み込まれていないか、初期化されず、および\) がありません。したがって失敗されていません。|  
  
## 解説  
 取得された識別子は [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) メソッドなどのスクリプトの実行スレッド コントロールのメソッドへの後続の呼び出しで使用できます。  
  
 このメソッドは、ベースの呼び出しによりオブジェクトをホストするまたは [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) のインターフェイスに非ベースのスレッドから外部に呼び出すことができます。  
  
## 参照  
 [IActiveScript](../../winscript/reference/iactivescript.md)