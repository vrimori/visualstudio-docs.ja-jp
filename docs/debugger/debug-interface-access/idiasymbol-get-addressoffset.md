---
title: "IDiaSymbol::get_addressOffset | Microsoft Docs"
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
  - "IDiaSymbol::get_addressOffset メソッド"
ms.assetid: c15639b0-7f37-46c7-891b-40273b7f6319
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_addressOffset
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

アドレス位置のオフセットの部分を取得します。  がに[LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)`LocIsStatic`設定されている場合はを使用します。  
  
## 構文  
  
```cpp#  
HRESULT get_addressOffset (   
   DWORD* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] アドレスの位置のオフセットの一部を返します。  
  
## 戻り値  
 が`S_OK`成功すると; それ以外の場合は`S_FALSE`エラー コード。  
  
> [!NOTE]
>  戻り値は`S_FALSE`プロパティがシンボルで使用できないことを意味します。  
  
## 解説  
 外部 DLL にある静的メンバーについて返されたオフセットはこのメソッドによってこのメソッドが仮想メンバーのアドレスの取得に依存すると同時に 0 である場合があります。  仮想アドレスは [IDiaSession](../../debugger/debug-interface-access/idiasession.md) のインターフェイス [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) のメソッドが DLL の読み込みアドレスを指定する以外のパラメーターという場合にのみ有効です。  
  
 アドレスのセクションの一部を取得するには[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md) のメソッドを呼び出します。  
  
## 必要条件  
  
|必要条件|Description|  
|----------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン :|DIA SDK v7.0|  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)   
 [IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)   
 [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)