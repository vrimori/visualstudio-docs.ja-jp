---
title: "IRemoteDebugApplication::EnumGlobalExpressionContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplication.EnumGlobalExpressionContexts
apilocation: pdm.dll
helpviewer_keywords: 
  - "IRemoteDebugApplication::EnumGlobalExpressionContexts"
ms.assetid: 61598a34-f409-42a2-810d-a9e92e2f4861
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IRemoteDebugApplication::EnumGlobalExpressionContexts
このアプリケーションで実行されるすべての言語に対するグローバル コンテキスト式を列挙します。  
  
## 構文  
  
```  
HRESULT EnumGlobalExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### パラメーター  
 `ppedec`  
 \[出力\]このアプリケーションで実行されるすべての言語に対するグローバル コンテキスト式を示す列挙子。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、このアプリケーションで実行されるすべての言語に対するグローバル コンテキスト式を列挙します。  
  
## 参照  
 [IRemoteDebugApplication インターフェイス](../../winscript/reference/iremotedebugapplication-interface.md)