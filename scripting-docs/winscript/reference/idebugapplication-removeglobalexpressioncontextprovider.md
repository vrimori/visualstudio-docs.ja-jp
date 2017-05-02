---
title: "IDebugApplication::RemoveGlobalExpressionContextProvider | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugApplication.RemoveGlobalExpressionContextProvider
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugApplication::RemoveGlobalExpressionContextProvider"
ms.assetid: ace638a3-ed34-4d20-8404-45c684aaaf1a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplication::RemoveGlobalExpressionContextProvider
このアプリケーションからグローバル コンテキスト式のプロバイダーを削除します。  
  
## 構文  
  
```  
HRESULT RemoveGlobalExpressionContextProvider(  
   DWORD_PTR  dwCookie  
);  
```  
  
#### パラメーター  
 `dwCookie`  
 \[入力\]クッキーは `AddGlobalExpressionContextProvider` のメソッドによってグローバル コンテキストのプロバイダーを追加したときに戻ります。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 `RemoveGlobalExpressionContextProvider` のメソッドは、このアプリケーションからグローバル コンテキスト式のプロバイダーを削除します。  
  
## 参照  
 [IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)   
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)