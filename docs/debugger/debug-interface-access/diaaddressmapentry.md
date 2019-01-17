---
title: DiaAddressMapEntry |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6cadfe96bc0bf0ac0395d93c2ef0b156b9965ed2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964086"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
アドレス マップ内のエントリについて説明します。  
  
## <a name="syntax"></a>構文  
  
```C++  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Elements  
 `rva`  
 A. イメージの相対仮想アドレス (RVA)  
  
 `rvaTo`  
 相対仮想アドレス`rva`B. イメージ内にマップされます  
  
## <a name="remarks"></a>コメント  
 アドレス マップは、(A) をもう 1 つ (B) 1 つのイメージのレイアウトからの翻訳を提供します。 配列の`DiaAddressMapEntry`構造体の順に並べ替えて`rva`アドレス マップを定義します。  
  
 アドレスに変換する`addrA`、イメージ アドレス内`addrB`B の図で、次の手順に従います。  
  
1. マップのエントリを検索`e`が大きいもの`rva`に等しいまたはそれよりも小さい`addrA`します。  
  
2. `delta = addrA - e.rva` を設定します。  
  
3. `addrB = e.rvaTo + delta` を設定します。  
  
   配列の`DiaAddressMapEntry`に構造体が渡される、 [idiaaddressmap::set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)メソッド。  
  
## <a name="requirements"></a>要件  
 ヘッダー: dia2.h  
  
## <a name="see-also"></a>「  
 [列挙型と構造体](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)