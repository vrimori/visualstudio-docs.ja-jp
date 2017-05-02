---
title: "IDebugApplication::HandleRuntimeError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.HandleRuntimeError
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::HandleRuntimeError"
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::HandleRuntimeError
現在のスレッドをブロックするに説明し、デバッガーの IDE にエラー通知を送信します。  
  
## 構文  
  
```  
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### パラメーター  
 `pErrorDebug`  
 \[入力\]発生したエラー。  
  
 `pScriptSite`  
 \[入力\]スレッドのスクリプトのサイト。  
  
 `pbra`  
 \[入力\]デバッガーでアプリケーションを再開したときに実行するアクション。  
  
 `perra`  
 \[入力\]エラーがある場合、デバッガーでアプリケーションを再開したときに実行するアクション。  
  
 `pfCallOnScriptError`  
 \[入力\]エンジンが `IActiveScriptSite::OnScriptError` のメソッドを呼び出すと `TRUE` であるフラグ。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 言語のエンジンは実行時エラーを引き起こすスレッドのコンテキストでこのメソッドを呼び出します。  このメソッドには、現在のスレッドはブロック、デバッガーの IDE に送信するエラー通知を送信します。  デバッガーの IDE がアプリケーションを再開すると、実行されるアクションを持つこのメソッドはを返します。  
  
> [!NOTE]
>  ランタイムの違反となり、タスクをする言語のエンジンは、スレッドには、などの列挙するスタック フレームが呼び出されることがあります。また、式を評価しますが、  
  
## 参照  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)   
 [IActiveScriptErrorDebug インターフェイス](../../winscript/reference/iactivescripterrordebug-interface.md)   
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)   
 [BREAKRESUMEACTION 列挙型](../../winscript/reference/breakresumeaction-enumeration.md)   
 [ERRORRESUMEACTION 列挙型](../../winscript/reference/errorresumeaction-enumeration.md)