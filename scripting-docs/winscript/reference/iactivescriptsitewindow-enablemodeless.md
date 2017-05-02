---
title: "IActiveScriptSiteWindow::EnableModeless | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteWindow.EnableModeless
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteWindow_EnableModeless"
ms.assetid: 83fe4f62-8e97-4f03-bc6f-d90aa888657d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow::EnableModeless
ホストをメイン ウィンドウ、またはモードレス ダイアログ ボックスを有効または無効にします。  
  
## 構文  
  
```  
HRESULT EnableModeless(  
    BOOL fEnable  // enable flag  
);  
```  
  
#### パラメーター  
 `fEnable`  
 \[入力\]フラグを設定して、`TRUE`場合は、メイン ウィンドウを有効にするには、モードレス ダイアログや、`FALSE`が、無効にする。  
  
## 戻り値  
 エラーが発生した場合、または `E_FAIL`が成功した場合 `S_OK` 返します。  
  
## 解説  
 このメソッドは `IOleInPlaceFrame::EnableModeless` のメソッドと同じものです。  
  
 このメソッドの呼び出しは入れ子にできます。  
  
## 参照  
 [IActiveScriptSiteWindow](../../winscript/reference/iactivescriptsitewindow.md)