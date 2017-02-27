---
title: "IDiaSession::findInlineeLinesByVA | Microsoft Docs"
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
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineeLinesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

クライアントが、指定した親シンボルによって、直接または間接的に、インライン展開され、指定された仮想アドレス \(VA\) に含まれるすべての関数の行番号情報を反復処理できる列挙型を取得します。  
  
## 構文  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           parent,  
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### パラメーター  
 `parent`  
 \[入力\] 親オブジェクトを表す `IDiaSymbol` オブジェクト。  
  
 `va`  
 \[入力\] VA としてアドレスを指定します。  
  
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