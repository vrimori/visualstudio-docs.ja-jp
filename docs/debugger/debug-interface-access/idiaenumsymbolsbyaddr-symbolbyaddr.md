---
title: "IDiaEnumSymbolsByAddr::symbolByAddr | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::symbolByAddr メソッド"
ms.assetid: 0b6f5a68-8402-4f29-8219-20576fda8166
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumSymbolsByAddr::symbolByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

イメージのセクション number とオフセットが参照を使用して列挙子を配置します。  
  
## 構文  
  
```cpp#  
HRESULT symbolByAddr (   
   DWORD**      isect,  
   DWORD**      offsect,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### パラメーター  
 isect  
 \[入力\] イメージ内のセクション number。  
  
 offsect  
 \[入力\] セクション オフセット。  
  
 ppsymbol  
 \[入力\] シンボルが検出した [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) を表すオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK` シンボルが見つからない場合 `S_FALSE` を返します。  それ以外の場合はエラー コード。  
  
## 参照  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)