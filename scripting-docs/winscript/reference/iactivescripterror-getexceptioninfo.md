---
title: "IActiveScriptError::GetExceptionInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetExceptionInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetExceptionInfo"
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetExceptionInfo
スクリプト エンジンがスクリプトの実行中に発生したエラーに関する情報を取得します。  
  
## 構文  
  
```  
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### パラメーター  
 `pexcepinfo`  
 \[入力\]エラー情報を受け取る `EXCEPINFO` の構造体のアドレス。  
  
## 戻り値  
 エラーが発生した場合、または `E_FAIL` が成功した場合 `S_OK` 返します。  
  
## 参照  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)