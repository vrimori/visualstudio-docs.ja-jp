---
title: "IActiveScriptError::GetSourcePosition | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptError.GetSourcePosition
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptError_GetSourcePosition"
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError::GetSourcePosition
スクリプト エンジンがスクリプトの実行中にエラーが発生したソース・コードの位置を取得します。  
  
## 構文  
  
```  
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### パラメーター  
 `pdwSourceContext`  
 \[入力\]コンテキストを識別するクッキーを受け取る変数のアドレス。  このパラメーターの解釈がホスト アプリケーションによって異なります。  
  
 `pulLineNumber`  
 \[入力\]エラーが発生したソース ファイルの行番号を受け取る変数のアドレス。  
  
 `pichCharPosition`  
 \[入力\]エラーが発生した行の文字位置を受け取る変数のアドレス。  
  
## 戻り値  
 場所が取得されていない場合、または `E_FAIL` が成功した場合 `S_OK` 返します。  
  
## 参照  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)