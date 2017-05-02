---
title: "IApplicationDebugger::onHandleBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebugger.onHandleBreakPoint
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebugger::onHandleBreakPoint"
ms.assetid: 31adcecd-d6c1-4222-ab2c-32ec2fefb322
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebugger::onHandleBreakPoint
ブレークポイント イベントを処理します。  
  
## 構文  
  
```  
HRESULT onHandleBreakPoint(  
   IRemoteDebugApplicationThread*  prpt,  
   BREAKREASON                     br,  
   IActiveScriptErrorDebug*        pError  
);  
```  
  
#### パラメーター  
 `prpt`  
 \[出力\]ブレークポイントが発生したスレッド。  
  
 `br`  
 \[出力\]ブレークポイントの理由。  
  
 `pError`  
 \[入力\] `br` の値が BREAKREASON\_ERROR である場合、ランタイム エラー情報。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、ブレークポイントがヒットし、`IDebugApplication::HandleBreakPoint` が呼び出されたときに呼び出されます。  
  
 アプリケーションは、デバッガーの IDE が `IRemoteDebugApplication::ResumeFromBreakPoint`を呼び出すまで中断されています。  
  
## 参照  
 [IApplicationDebugger インターフェイス](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)   
 [IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)   
 [BREAKREASON 列挙型](../../winscript/reference/breakreason-enumeration.md)