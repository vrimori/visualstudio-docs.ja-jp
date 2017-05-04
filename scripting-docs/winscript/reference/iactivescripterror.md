---
title: "IActiveScriptError | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptError インターフェイス"
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptError
このインターフェイスを実装するオブジェクトです [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) のメソッドにスクリプト エンジンが処理されないエラーを検出するたびに渡されます。  ホストは、発生したエラーに関する情報を取得するために、このオブジェクトのメソッドを呼び出します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|エラーに関する情報を取得します。|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|エラーが発生したソース・コードの位置を取得します。|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|エラーが発生したソース ファイル行を取得します。|  
  
## 参照  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)