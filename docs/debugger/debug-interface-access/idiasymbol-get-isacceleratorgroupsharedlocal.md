---
title: "IDiaSymbol::get_isAcceleratorGroupSharedLocal | Microsoft Docs"
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
ms.assetid: 17a20542-5b45-478f-bb80-0d56031aadb5
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSymbol::get_isAcceleratorGroupSharedLocal
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

シンボルは、. AMP C\+\+ のアクセラレータ用にコンパイルされたコード グループの共有ローカル変数に対応するかどうかを示すフラグを取得します。  
  
## 構文  
  
```cpp  
HRESULT get_isAcceleratorGroupSharedLocal(   
   BOOL* pFlag);  
```  
  
#### パラメーター  
 `pFlag`  
 \[入力\] シンボルが C \+\+. AMP のアクセラレータ用にコンパイルされたコード グループの共有ローカル変数に対応するかどうかを示す `BOOL` へのポインター。  変数の格納場所の情報を取得して入力に `TRUE`、`get_baseDataSlot` と `get_baseDataOffset` のメソッドを使用できます。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合は `S_FALSE` またはエラー コードを返します。  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)   
 [IDiaSymbol::get\_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)