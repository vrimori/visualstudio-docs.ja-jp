---
title: "SCRIPTTRACEINFO 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# SCRIPTTRACEINFO 列挙型
トレースするスクリプトのイベントを表します。  [IActiveScriptSiteTraceInfo::SendScriptTraceInfo メソッド](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md)で使用します。  
  
## 構文  
  
```  
typedef enum tagSCRIPTTRACEINFO {    
    SCRIPTTRACEINFO_SCRIPTSTART = 0,    
    SCRIPTTRACEINFO_SCRIPTEND   = 1,    
    SCRIPTTRACEINFO_COMCALLSTART    = 2,    
    SCRIPTTRACEINFO_COMCALLEND  = 3,    
    SCRIPTTRACEINFO_CREATEOBJSTART  = 4,    
    SCRIPTTRACEINFO_CREATEOBJEND    = 5,    
    SCRIPTTRACEINFO_GETOBJSTART = 6,    
    SCRIPTTRACEINFO_GETOBJEND   = 7,    
} SCRIPTTRACEINFO ;  
```  
  
## 列挙値  
  
|||  
|-|-|  
|SCRIPTTRACEINFO\_SCRIPTSTART|スクリプトの開始。|  
|SCRIPTTRACEINFO\_SCRIPTEND|スクリプトの最後。|  
|SCRIPTTRACEINFO\_COMCALLSTART|COM 呼び出しの開始。|  
|SCRIPTTRACEINFO\_COMCALLEND|COM 呼び出しの最後。|  
|SCRIPTTRACEINFO\_CREATEOBJSTART|オブジェクトの作成の開始。|  
|SCRIPTTRACEINFO\_CREATEOBJEND|オブジェクトの作成が終了します。|  
|SCRIPTTRACEINFO\_GETOBJSTART|GetObject の呼び出しの開始。|  
|SCRIPTTRACEINFO\_GETOBJEND|GetObject 呼び出しの最後。|