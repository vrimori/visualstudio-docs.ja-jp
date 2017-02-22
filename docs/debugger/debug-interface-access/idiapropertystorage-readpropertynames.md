---
title: "IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaPropertyStorage::ReadPropertyNames"
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定したプロパティ識別子の対応する文字列名を取得します。  
  
## 構文  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### パラメーター  
 `cpropid`  
 \[入力\] `rgpropid` のプロパティ ID の数。  
  
 `rgpropid`  
 \[出力\] 名前を取得するプロパティ ID の配列 \(`PROPID` は `ULONG` と WTypes.h で定義されます\)。  
  
 `rglpwstrName`  
 \[入力出力\] 指定したプロパティの ID プロパティ名の配列。  配列にはプロパティ名の要求された数を保持する割り当てされていて少なくとも `cpropid``BSTR` の文字列を保持する必要があります。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  
  
## 解説  
 返されたプロパティ名が不要になったときに解放する必要があります。`SysFreeString` の関数を呼び出します\)。  
  
## 参照  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)