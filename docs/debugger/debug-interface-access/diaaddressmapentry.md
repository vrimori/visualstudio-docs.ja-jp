---
title: "DiaAddressMapEntry | Microsoft Docs"
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
  - "DiaAddressMapEntry 列挙型"
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Address マップのエントリについて説明します。  
  
## 構文  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## Elements  
 `rva`  
 イメージは \(RVA\). の相対仮想アドレス。  
  
 `rvaTo`  
 相対仮想アドレス `rva` はイメージの 12 C にマップされます。  
  
## 解説  
 Address マップは1 種類のイメージのレイアウト \(\) で区切ります \(b\) に移動を提供します。  `rva` で並べ替えて `DiaAddressMapEntry` の構造体の配列はアドレスのマップを定義します。  
  
 アドレスへのアドレスはイメージの `addrA` は`addrB` 変換するにはイメージの 12 C で次の手順が実行されます :  
  
1.  エントリ `addrA`以下の最大 `rva` の `e` をマップを検索します。  
  
2.  `delta = addrA – e.rva` を設定します。  
  
3.  `addrB = e.rvaTo + delta` を設定します。  
  
 `DiaAddressMapEntry` の構造体の配列は [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) のメソッドに渡されます。  
  
## 必要条件  
 ヘッダー : dia2.h  
  
## 参照  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)