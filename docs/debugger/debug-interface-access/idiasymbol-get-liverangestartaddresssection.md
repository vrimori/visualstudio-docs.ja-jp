---
title: "IDiaSymbol::get_liveRangeStartAddressSection | Microsoft Docs"
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
  - "IDiaSymbol::get_liveRangeStartAddressSection"
ms.assetid: 892b80ff-5957-4233-b4d7-6144167be289
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_liveRangeStartAddressSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ローカル シンボルが有効である範囲の開始アドレスのセクションの一部を返します。  
  
## 構文  
  
```cpp#  
HRESULT get_liveRangeStartAddressSection (   
   DWORD* section  
);  
```  
  
#### パラメーター  
 `section`  
 \[入力\] 開始アドレス範囲のセクションの一部を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
> [!NOTE]
>  返されるエラー コードはシンボルに有効な範囲の情報がないことを示します。  
  
## 解説  
 セクション オフセットとしてアドレスはシンボルが有効範囲の先頭。  
  
 アドレスのオフセットの一部を取得するには[IDiaSymbol::get\_liveRangeStartAddressOffset](../Topic/IDiaSymbol::get_liveRangeStartAddressOffset.md) を使用します。  
  
## 必要条件  
 ヘッダー : Dia2.h  
  
 ライブラリ : diaguids.lib  
  
 DLL: msdia100.dll  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)