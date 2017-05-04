---
title: "IActiveScriptSiteTraceInfo::SendScriptTraceInfo メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptSiteTraceInfo::SendScriptTraceInfo メソッド
イベントの種類、コンテキストおよびスクリプトのステートメントを含む送信のトレース情報。  
  
## 構文  
  
```  
HRESULT SendScriptTraceInfo(   
    [in] SCRIPTTRACEINFO stiEventType,   
    [in] GUID guidContextID,   
    [in] DWORD dwScriptContextCookie,   
    [in] LONG lScriptStatementStart,   
    [in] LONG lScriptStatementEnd,   
    [in] DWORD64 dwReserved   
);   
```  
  
#### パラメーター  
 `stiEventType`  
 イベントの種類。  
  
 `guidContextId`  
 コンテキストの GUID。  
  
 `dwScriptContextCookie`  
 コンテキスト クッキー。  
  
 `lScriptStatementStart`  
 スクリプトのステートメントの開始位置。  
  
 `lScriptStatementEnd`  
 スクリプトのステートメントの最後の位置。  
  
 `dwReserved`  
 予約されています。