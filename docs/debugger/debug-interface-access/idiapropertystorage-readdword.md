---
title: "IDiaPropertyStorage::ReadDWORD | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadDWORD"
ms.assetid: 5f4c034e-a9d3-4560-94b5-ede524741439
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadDWORD
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロパティの `DWORD` の値を読み取ります。  
  
## 構文  
  
```cpp#  
HRESULT ReadDWORD (   
   PROPID id,  
   DWORD* pValue  
);  
```  
  
#### パラメーター  
 `id`  
 \[入力\] 読み込まれるプロパティ識別子 \(`PROPID` は `ULONG` と WTypes.h で定義されます\)。  
  
 `pValue`  
 \[入力\] プロパティ値を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  プロパティは型である `DWORD``E_INVALIDARG` を返します。  
  
## 解説  
 `DWORD` は 32 ビットの符号なし整数と Windows によって定義されます。  
  
## 参照  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)