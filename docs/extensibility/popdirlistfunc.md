---
title: "POPDIRLISTFUNC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "POPLISTFUNC"
helpviewer_keywords: 
  - "POPDIRLISTFUNC コールバック関数"
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

これに指定されたコールバック関数、 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) ディレクトリおよび \(必要に応じて\) を検索するソース管理下にファイル名のコレクションを更新する関数。  
  
 `POPDIRLISTFUNC` コールバックは、これらのディレクトリとファイル名に対してのみ呼び出す必要があります \(に指定された一覧で、 `SccPopulateDirList` 関数\)、ソース管理下に実際にします。  
  
## Signature  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)( LPVOID pvCallerData, BOOL bFolder, LPCSTR lpDirectoryOrFileName );  
```  
  
## パラメーター  
 pvCallerData  
 \[in\]渡されたユーザー値 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)です。  
  
 bFolder  
 \[in\] `TRUE` 場合に名前 `lpDirectoryOrFileName` ディレクトリは、それ以外の場合、名前は、ファイル名。  
  
 lpDirectoryOrFileName  
 \[in\]ソース コード管理下にあるディレクトリまたはファイル名への完全なローカル パス。  
  
## 戻り値  
 IDE には、該当するエラー コードが返されます。  
  
|値|説明|  
|-------|--------|  
|SCC\_OK|処理を続行します。|  
|SCC\_I\_OPERATIONCANCELED|処理を停止します。|  
|SCC\_E\_xxx|適切なソース制御エラーは、処理を停止する必要があります。|  
  
## 解説  
 場合、 `fOptions` のパラメーター、 `SccPopulateDirList` が含まれている、 `SCC_PDL_INCLUDEFILES` フラグで、一覧はファイル名だけでなく、ディレクトリの名前を含む可能性があります。  
  
## 参照  
 [IDE で実装されるコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [エラー コード](../extensibility/error-codes.md)