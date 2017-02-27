---
title: "IDiaSymbol::get_platform | Microsoft Docs"
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
  - "IDiaSymbol::get_platform メソッド"
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_platform
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

コンパイル単位がコンパイルされるプラットフォームの種類を取得します。  
  
## 構文  
  
```cpp#  
HRESULT get_platform (   
   DWORD* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] コンパイル単位がコンパイルされるプラットフォームの種類を指定する [CV\_CPU\_TYPE\_e 列挙型](../../debugger/debug-interface-access/cv-cpu-type-e.md) の列挙型の値を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合戻り `S_FALSE` またはエラー コード。  
  
> [!NOTE]
>  `S_FALSE` の戻り値はプロパティのシンボルで使用できないことを意味します。  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV\_CPU\_TYPE\_e 列挙型](../../debugger/debug-interface-access/cv-cpu-type-e.md)