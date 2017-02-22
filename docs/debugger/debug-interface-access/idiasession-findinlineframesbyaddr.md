---
title: "IDiaSession::findInlineFramesByAddr | Microsoft Docs"
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
ms.assetid: e7dc1ac7-bb09-45be-96d2-365a9b7336e4
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineFramesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

クライアントが特定のアドレスのインライン フレームすべての反復処理できる列挙型を取得します。  
  
## 構文  
  
```cpp#  
HRESULT findInlineFramesByAddr (   
   IDiaSymbol*       parent,  
   DWORD             isect,  
   DWORD             offset,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### パラメーター  
 `parent`  
 \[入力\] 親オブジェクトを表す `IDiaSymbol` オブジェクト。  
  
 `isect`  
 \[入力\] アドレスのセクション要素を指定します。  
  
 `offset`  
 \[入力\] アドレスのオフセット要素を指定します。  
  
 `ppResult`  
 \[出力\] 取得されたフレームの一覧を含む `IDiaEnumSymbols` のオブジェクトを保持します。  
  
## 戻り値  
 成功した場合は `S_OK` を返し、それ以外の場合はエラー コードを返します。  
  
## 参照  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)