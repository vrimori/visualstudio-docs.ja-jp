---
title: "IDiaSession::findInlineFramesByRVA | Microsoft Docs"
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
ms.assetid: ddb3ff0e-cb3d-4fa0-af56-f064b218b264
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineFramesByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

クライアントが指定した相対仮想アドレス \(RVA\) のインライン フレームすべての反復処理できる列挙型を取得します。  
  
## 構文  
  
```cpp#  
HRESULT findInlineFramesByRVA (   
   IDiaSymbol*       parent,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### パラメーター  
 `parent`  
 \[入力\] 親オブジェクトを表す `IDiaSymbol` オブジェクト。  
  
 `rva`  
 \[出力\] RVA としてアドレスを指定します。  
  
 `ppResult`  
 \[出力\] 取得されたフレームの一覧を含む `IDiaEnumSymbols` のオブジェクトを保持します。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合はエラー コードを返します。  
  
## 参照  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)