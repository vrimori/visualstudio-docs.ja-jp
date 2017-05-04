---
title: "IActiveScript::InterruptScriptThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.InterruptScriptThread
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_InterruptScriptThread"
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::InterruptScriptThread
実行中のスクリプトのスレッド \(イベント シンク、即時実行、またはマクロ呼び出し\) で実行を中断します。  このメソッドは、スタックするスクリプトを終了するために使用できます \(たとえば、無限ループに\)。  これは、ベースの呼び出しによりオブジェクトをホストするまたは [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) のメソッドに非ベースのスレッドから外部に呼び出すことができます。  
  
## 構文  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### パラメーター  
 `stidThread`  
 \[入力\]中断するスレッドの ID または特別なスレッド識別子の 1 つが評価します:  
  
|値|説明|  
|-------|--------|  
|SCRIPTTHREADID\_ALL|すべてのスレッド。  中断がすべてのスクリプト メソッドの処理中に現在適用されます。  スクリプトは、ドロップ呼び出し元が SCRIPTSTATE\_DISCONNECTED または SCRIPTSTATE\_INITIALIZED のフラグの設定による [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) のメソッドを呼び出して、再度実行することを、次のスクリプト化されたイベントによりスクリプト コード要求されない点に注意してください。|  
|SCRIPTTHREADID\_BASE|基本スレッド; つまり、スクリプト エンジンのインスタンスが作成されたスレッド。|  
|SCRIPTTHREADID\_CURRENT|現在実行中のスレッド。|  
  
 `pexcepinfo`  
 \[入力\]中止スクリプトに報告されるエラー情報を含む `EXCEPINFO` の構造体のアドレス。  
  
 `dwFlags`  
 \[入力\]オプション フラグは中断に関連付けられています。  次のいずれかの値を指定します。  
  
|値|説明|  
|-------|--------|  
|SCRIPTINTERRUPT\_DEBUG|現在サポートされている場合、スクリプトの実行ポイントにスクリプト エンジンのデバッガーを入力します。|  
|SCRIPTINTERRUPT\_RAISEEXCEPTION|スクリプト エンジンの言語でサポートされている場合、スクリプトで例外を処理するようにします。  それ以外の場合は、スクリプト メソッドは中止され、エラー コードが呼び出し元に返されます。; つまり、イベント ソースまたはマクロの呼び出し元。|  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが想定されていません \(たとえば、スクリプト エンジンはまだ読み込まれていないか、初期化されていません\)。|  
  
## 参照  
 [IActiveScript](../../winscript/reference/iactivescript.md)