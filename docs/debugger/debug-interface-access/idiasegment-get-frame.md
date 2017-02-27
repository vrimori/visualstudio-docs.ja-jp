---
title: "IDiaSegment::get_frame | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSegment::get_frame メソッド"
ms.assetid: 9fece9c7-064a-4d6b-9cef-fc387f322205
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSegment::get_frame
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

区分数を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_frame (   
   DWORD* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] 区分番号を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` このプロパティをサポートする必要 `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)