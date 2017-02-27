---
title: "OPTNAMECHANGEPFN | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OPTNAMECHANGEPFN"
helpviewer_keywords: 
  - "OPTNAMECHANGEPFN コールバック関数"
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

これへの呼び出しで指定されたコールバック関数、 [SccSetOption](../extensibility/sccsetoption-function.md) \(オプションを使用して `SCC_OPT_NAMECHANGEPFN`\) によるソース管理プラグイン IDE に戻る名前変更を通知するために使用します。  
  
## Signature  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)( LPVOID pvCallerData, LPCSTR pszOldName, LPCSTR pszNewName );  
```  
  
## パラメーター  
 pvCallerData  
 \[in\]以前の呼び出しで指定されたユーザーの値、 [SccSetOption](../extensibility/sccsetoption-function.md) \(オプションを使用して `SCC_OPT_USERDATA`\)。  
  
 pszOldName  
 \[in\]ファイルの元の名前。  
  
 pszNewName  
 \[in\]\[ファイル名に変更されました。  
  
## 戻り値  
 なし。  
  
## 解説  
 ソース管理操作中に、ファイルの名前を変更する場合、ソース管理プラグインはこのコールバックから名前の変更は IDE を通知できます。  
  
 IDE がこのコールバックをサポートしていない場合を呼び出さない、 [SccSetOption](../extensibility/sccsetoption-function.md) を指定します。 かどうか、プラグインをサポートしていないこのコールバックが返されます `SCC_E_OPNOTSUPPORTED` から、 `SccSetOption` IDE がコールバックを設定しようとしたときに機能します。  
  
## 参照  
 [IDE で実装されるコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)