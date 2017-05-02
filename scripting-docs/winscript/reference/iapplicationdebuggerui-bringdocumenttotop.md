---
title: "IApplicationDebuggerUI::BringDocumentToTop | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IApplicationDebuggerUI.BringDocumentToTop
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IApplicationDebuggerUI::BringDocumentToTop"
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IApplicationDebuggerUI::BringDocumentToTop
デバッガーのユーザー インターフェイスにデバッグ指定のドキュメントを含む上にウィンドウが表示されます。  
  
## 構文  
  
```  
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### パラメーター  
 `pddt`  
 \[入力\]デバッガーのユーザー インターフェイスの上部に表示されるようにドキュメントをデバッグします。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_INVALIDARG`|ドキュメントが不明な場合。|  
  
## 解説  
 このメソッドは、上にデバッガーのユーザー インターフェイスで指定したデバッグのドキュメントを含むウィンドウが表示されます。  
  
## 参照  
 [IApplicationDebuggerUI インターフェイス](../../winscript/reference/iapplicationdebuggerui-interface.md)