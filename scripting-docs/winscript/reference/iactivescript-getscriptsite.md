---
title: "IActiveScript::GetScriptSite | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.GetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_GetScriptSite"
ms.assetid: 83a2a89d-93d0-4cbd-9244-91a730cb406b
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IActiveScript::GetScriptSite
Windows のスクリプト エンジンに関連付けられたサイトのオブジェクトを取得します。  
  
## 構文  
  
```  
HRESULT GetScriptSite(  
    REFIID iid,           // interface identifier  
    void **ppvSiteObject  // address of host site interface  
);  
```  
  
#### パラメーター  
 `iid`  
 \[入力\]要求されたインターフェイスの識別子。  
  
 `ppvSiteObject`  
 \[出力\]ホスト サイトのオブジェクトへのインターフェイス ポインターを受け取る場所のアドレス。  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_NOINTERFACE`|特定のインターフェイスはサポートされていません。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`S_FALSE`|サイトが設定された; `ppvSiteObject` のパラメーターは `NULL`に設定されます。|  
  
## 参照  
 [IActiveScript](../../winscript/reference/iactivescript.md)