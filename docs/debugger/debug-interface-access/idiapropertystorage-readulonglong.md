---
title: "IDiaPropertyStorage::ReadULONGLONG | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadULONGLONG"
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

プロパティの `ULONGLONG` の値を読み取ります。  
  
## 構文  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### パラメーター  
 `id`  
 \[入力\] 読み込まれるプロパティ識別子 \(`PROPID` は `ULONG` と WTypes.h で定義されます\)。  
  
 `pValue`  
 \[入力\] プロパティ値を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  プロパティは型である `ULONGLONG``E_INVALIDARG` を返します。  
  
## 解説  
 `ULONGLONG` は 64 ビットの符号なし整数と Windows によって定義されます。  
  
## 参照  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)