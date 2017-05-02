---
title: "SCRIPTTHREADSTATE 列挙型 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: SCRIPTTHREADSTATE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SCRIPTTHREADSTATE 列挙型"
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# SCRIPTTHREADSTATE 列挙型
スクリプト エンジンでスレッドの状態を指定します。  この列挙体は [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) メソッドで使用されます。  
  
## 構文  
  
```  
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## 列挙値  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE\_NOTINSCRIPT|指定したスレッドが現在スクリプト化されたイベントを処理しないか、すぐに実行されるスクリプトのテキストを、スクリプトのマクロを実行しません。|  
|SCRIPTTHREADSTATE\_RUNNING|指定したスレッドは積極的にスクリプト化されたイベントを処理し、すぐに実行されるスクリプトのテキストを、スクリプトのマクロを実行します。|  
  
## 参照  
 [アクティブ スクリプトの定数、列挙型、およびエラー コード](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)