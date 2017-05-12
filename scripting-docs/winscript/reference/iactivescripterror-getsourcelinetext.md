---
title: "IActiveScriptError::GetSourceLineText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourceLineText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourceLineText"
ms.assetid: 64f7f37f-7288-4dbe-b626-a35d90897f36
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourceLineText
スクリプト エンジンがスクリプトの実行中にエラーが発生したソース ファイル行を取得します。  
  
## 構文  
  
```  
HRESULT GetSourceLineText(  
    BSTR *pbstrSourceLine  // address of buffer for source line  
);  
```  
  
## パラメーター  
 `pbstrSourceLine`  
 \[入力\]エラーが発生したソース・コードの行を受け取るバッファーのアドレス。  
  
## 戻り値  
 ソース ファイルの行が取得されていない場合、または `E_FAIL` が成功した場合 `S_OK` 返します。  
  
## 参照  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)