---
title: "IActiveScriptAuthor::GetEventHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetEventHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetEventHandler"
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetEventHandler
指定した属性を持つスクリプトレットを返します。  
  
## 構文  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### パラメーター  
 `pdisp`  
 \[入力\]スクリプトレットがアタッチされている `NamedItem` に対応する `IDispatch` のオブジェクト。  
  
 `pszItem`  
 \[出力\]ホストの完全修飾名スクリプトレットのトップレベルの識別子のバッファーのアドレス。  
  
 `pszSubItem`  
 \[出力\]ホストの完全修飾名スクリプトレットの 2 番目のレベルの識別子のバッファーのアドレス。  名前に 1 レベルのみの場合に無効にする。  
  
 `pszEvent`  
 \[入力\]イベント名を含むバッファーのアドレス。  スクリプトレットは、このイベントのイベント ハンドラーです。  
  
 `ppse`  
 \[出力\]指定した属性を持つスクリプトレットの `IScriptEntry` のインターフェイスへのポインターを受け取る変数のアドレス。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)