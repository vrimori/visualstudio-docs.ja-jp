---
title: "IDiaPropertyStorage::ReadBSTR | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadBSTR"
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadBSTR
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロパティの `BSTR` の値を読み取ります。  
  
## 構文  
  
```cpp#  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### パラメーター  
 `id`  
 \[入力\] 読み込まれるプロパティ識別子 \(`PROPID` は `ULONG` と WTypes.h で定義されます\)。  
  
 `pValue`  
 \[入力\] プロパティ値を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  プロパティは型である `BSTR``E_INVALIDARG` を返します。  
  
## 解説  
 `BSTR` で終了するワイド文字列と Windows によって定義されます。  
  
## 参照  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)