---
title: "IDiaSymbol::get_hasLongJump | Microsoft Docs"
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
  - "IDiaSymbol::get_hasLongJump メソッド"
ms.assetid: 14484cb1-43b0-47a1-a9a8-081b55566886
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_hasLongJump
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

関数は [longjmp](/visual-cpp/c-runtime-library/reference/longjmp) のコマンドを使用しているかどうかを指定するフラグを取得します。[setjmp](/visual-cpp/c-runtime-library/reference/setjmp) のコマンドと例外処理の C スタイルの組み合わせメソッドとなります\)。  
  
## 構文  
  
```cpp#  
HRESULT get_hasLongJump  
   BOOL *pFlag  
);  
```  
  
#### パラメーター  
 `pFlag`  
 \[入力\] 関数が `longjmp` のコマンドが含まれる場合はを返します `TRUE` ; それ以外の場合戻り `FALSE`。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合戻り `S_FALSE` またはエラー コード。  
  
> [!NOTE]
>  `S_FALSE` の戻り値はプロパティのシンボルで使用できないことを意味します。  
  
## 必要条件  
  
|必要条件|Description|  
|----------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン :|DIA SDK v8.0|  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)   
 [longjmp](/visual-cpp/c-runtime-library/reference/longjmp)   
 [setjmp](/visual-cpp/c-runtime-library/reference/setjmp)