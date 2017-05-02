---
title: "IActiveScriptTraceInfo::StartScriptTracing メソッド | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IActiveScriptTraceInfo::StartScriptTracing メソッド
開始スクリプトのトレース。  
  
## 構文  
  
```  
HRESULT StartScriptTracing(   
    [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,   
    [in] GUID guidContextID   
);  
  
```  
  
#### パラメーター  
 `pSiteTraceInfo`  
 ホストの IActiveScriptSiteTraceInfo へのポインター。  
  
 `guidContextId`  
 コンテキストの GUID。  
  
## 戻り値  
 このメソッドの使用可能な戻り値は、です:  
  
1.  S\_OK: 成功。  
  
2.  : E\_POINTER `pSiteTraceInfo` が null ポインターです。  
  
3.  E\_NOTIMPL: 実行されません。