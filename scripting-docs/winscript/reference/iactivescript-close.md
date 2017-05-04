---
title: "IActiveScript::Close | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Close
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Close"
ms.assetid: cc7dd63b-1d7e-410a-857b-09ea3aade275
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::Close
したがって、スクリプト エンジンを現在読み込まれているスクリプトを破棄し、状態を失い、によって他のオブジェクトのインターフェイス ポインターを解放するためにを呼び出した場合、終了済みの状態になります。  イベント シンク、すぐに実行されるスクリプトのテキストと既に進行中のマクロ呼び出しは、状態の変更 \(実行中のスクリプトのスレッドを取り消す使用 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md) \) の前に実行されます。  このメソッドは、作成のホストによって循環参照問題を防ぐためにインターフェイスが解放される前に呼び出す必要があります。  
  
## 構文  
  
```  
HRESULT Close(void);  
```  
  
## 戻り値  
 次の値の場合: 1  
  
|値|説明|  
|-------|--------|  
|`S_OK`|成功。|  
|`E_UNEXPECTED`|呼び出しが想定されていません \(たとえば、スクリプト エンジンが終了状態には既に存在していました\)。|  
|`OLESCRIPT_S_PENDING`|メソッドは正常に列を実行しましたが、状態は変更しません。  状態の変化が、サイト [IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md) のメソッドで呼び出される必要があります。|  
|`S_FALSE`|メソッドが成功するスクリプトはまだ閉じられています。|  
  
## 参照  
 [IActiveScript](../../winscript/reference/iactivescript.md)