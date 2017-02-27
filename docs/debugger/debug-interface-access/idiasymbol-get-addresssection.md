---
title: "IDiaSymbol::get_addressSection | Microsoft Docs"
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
  - "IDiaSymbol::get_addressSection メソッド"
ms.assetid: fe80d479-3bb5-4f55-9b62-1bd58d0a60ce
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_addressSection
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

アドレス位置のセクションの部分を取得します。  [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)`LocIsStatic` がに設定されている場合はを使用します。  
  
## 構文  
  
```cpp#  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### パラメーター  
 `pRetVal`  
 \[入力\] アドレスの位置のセクションの一部を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合戻り `S_FALSE` またはエラー コード。  
  
> [!NOTE]
>  `S_FALSE` の戻り値はプロパティのシンボルで使用できないことを意味します。  
  
## 解説  
 外部 DLL にある静的メンバーについて返されたセクションではこのメソッドによってこのメソッドが仮想メンバーのアドレスの取得に依存すると同時に 0 である場合があります。  仮想アドレスは [IDiaSession](../../debugger/debug-interface-access/idiasession.md) のインターフェイス [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) のメソッドが DLL の読み込みアドレスを指定する以外のパラメーターという場合にのみ有効です。  
  
 アドレスのオフセットの一部を取得するには[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md) のメソッドを呼び出します。  
  
## 必要条件  
  
|必要条件|Description|  
|----------|-----------------|  
|ヘッダー:|dia2.h|  
|バージョン :|DIA SDK v7.0|  
  
## 参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)