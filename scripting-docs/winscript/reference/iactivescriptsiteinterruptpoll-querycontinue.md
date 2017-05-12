---
title: "IActiveScriptSiteInterruptPoll::QueryContinue | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteInterruptPoll.QueryContinue
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteInterruptPoll::QueryContinue"
ms.assetid: 41ac3807-f8b4-4a0e-bcc6-556bc89f3904
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteInterruptPoll::QueryContinue
ホストがスクリプトが終了することを指定できます。  
  
## 構文  
  
```  
HRESULT QueryContinue();  
```  
  
#### パラメーター  
 このメソッドは、パラメーターを受け取りません。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|呼び出しが成功し、ホストはスクリプトの実行が継続されます。|  
|`S_FALSE`|呼び出しが成功し、スクリプトが終了するようにホストに要求します。|  
  
## 解説  
 ホストされたスクリプトは `QueryContinue` でメソッドの戻り値がである `S_OK`終了する必要があります。  `S_FALSE` の戻り値は、スクリプトが終了すると、ホスト上で明示的に要求示します。  
  
 マルチスレッドのホストはスクリプトを終了するに `IActiveScript::InterruptScriptThread` のメソッドを使用する場合もあります。  
  
## 参照  
 [IActiveScriptSiteInterruptPoll インターフェイス](../../winscript/reference/iactivescriptsiteinterruptpoll-interface.md)   
 [IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)