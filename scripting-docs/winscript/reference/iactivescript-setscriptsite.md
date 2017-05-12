---
title: "IActiveScript::SetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_SetScriptSite"
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScript::SetScriptSite
ホストによって提供される [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) のインターフェイスのサイトをスクリプト エンジンに通知します。  他の [IActiveScript](../../winscript/reference/iactivescript.md) のインターフェイス メソッドが使用する前にこのメソッドを呼び出します。  
  
## 構文  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### パラメーター  
 `pScriptSite`  
 \[出力\]このスクリプト エンジンのインスタンスに関連付けられるホストから提供されるスクリプトのサイトのアドレス。  サイトは、このスクリプト エンジンのインスタンスに固有に割り当てられている; そのほかのスクリプト エンジンによって共有できません。  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_FAIL`|未定義のエラーが発生しました; スクリプト エンジンは、サイトの初期化を完了のできませんでした。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが想定されていません \(たとえば、サイトが既に設定されています\)。|  
  
## 参照  
 [IActiveScript](../../winscript/reference/iactivescript.md)