---
title: "IDiaSession::findInlineeLinesByAddr | Microsoft Docs"
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
ms.assetid: bb70e408-eed1-4c9c-b5b1-44323125f48b
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineeLinesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

クライアントが、指定した親シンボルによって、直接または間接的に、インライン展開され、指定したアドレスの範囲に含まれるすべての関数の行番号情報を反復処理できる列挙型を取得します。  
  
## 構文  
  
```cpp#  
HRESULT findInlineeLinesByAddr (   
   IDiaSymbol*           parent,  
   DWORD                 isect,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### パラメーター  
 `parent`  
 \[入力\] 親オブジェクトを表す `IDiaSymbol` オブジェクト。  
  
 `isect`  
 \[入力\] アドレスのセクション要素を指定します。  
  
 `offset`  
 \[入力\] アドレスのオフセット要素を指定します。  
  
 `length`  
 \[入力\] のバイト数、アドレス範囲をこのクエリでカバーするを指定します。  
  
 `ppResult`  
 \[出力\] 取得された行番号の一覧を含む `IDiaEnumLineNumbers` のオブジェクトを保持します。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合はエラー コードを返します。  
  
## 参照  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)