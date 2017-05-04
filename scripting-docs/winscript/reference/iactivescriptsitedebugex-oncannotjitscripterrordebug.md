---
title: "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebugEx.OnCanNotJITScriptErrorDebug
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug"
ms.assetid: 83f81476-bf12-47f2-897d-1d37d21137d4
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug
プロセス デバッグ マネージャーで時間のスクリプト デバッガーのを検索しない場合、スクリプトの実行時エラーについてホストに通知します。  
  
 、ホスト上でデバッガーを実行するには、[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)を処理する必要があります。  ユーザー アクションに基づいて、ホストはデバッガーと戻り値をアタッチするか、OnScriptErrorDebug `pfEnterDebugger` のパラメーターのデバッガーの起動を返します。  プロセス デバッグ マネージャーによって解釈できる外部デバッガーがない場合でも、実行時エラーに関する通知を取得するには、このインターフェイスを実装します。  
  
## 構文  
  
```  
HRESULT OnCanNotJITScriptErrorDebug(  
   IActiveScriptErrorDebug*  pErrorDebug  
   BOOL *pfCallOnScriptErrorWhenContinuing  
);  
```  
  
#### パラメーター  
 `pErrorDebug`  
 \[入力\]実行時エラー発生した。  
  
 `pfCallOnScriptErrorWhenContinuingt`  
 ユーザーがデバッグを継続する場合 [IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md) を呼び出すするかどうか。\[入力\]  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 また、通知を受け取るには、このインターフェイスを実装します。  
  
## 参照  
 [IActiveScriptSiteDebugEx インターフェイス](../../winscript/reference/iactivescriptsitedebugex-interface.md)