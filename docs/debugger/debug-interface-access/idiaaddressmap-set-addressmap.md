---
title: Idiaaddressmap::set_addressmap |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_addressMap method
ms.assetid: 81e82073-089b-43d5-af39-49d7a4907c7a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a1c934dc998818973b5de4106c3df952ad24f22f
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31461042"
---
# <a name="idiaaddressmapsetaddressmap"></a>IDiaAddressMap::set_addressMap
イメージのレイアウトの翻訳をサポートするために、アドレス マップを提供します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT set_addressMap (   
   DWORD                     cbData,  
   struct DiaAddressMapEntry data[],  
   BOOL                      imagetoSymbols  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cbData`  
 [in]内の要素の数、`data`パラメーター。  
  
 `data[]`  
 [in]配列[DiaAddressMapEntry 構造体](../../debugger/debug-interface-access/diaaddressmapentry.md)変換マップを定義する構造体。  
  
 `imagetoSymbols`  
 [in]`TRUE`場合、 `data` (デバッグ シンボルで記述された) としてパラメーターを新しいイメージのレイアウトから元のレイアウトへのマップを定義します。 `FALSE` 場合`data`の元のレイアウトから取得した新しいイメージのレイアウトにマップします。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 通常、DIA は、プログラム データベース (.pdb) ファイルからアドレス変換マップを取得します。 これらの値は、不足している場合、 [idiaaddressmap::set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)メソッドは、2 回呼び出されますが 1 回、`imagetoSymbols`パラメーターに設定`TRUE`とが 1 回、`imagetoSymbols`パラメーターに設定`FALSE`です。 使用してアドレスのマップの変換を有効にすることはできません、 [idiaaddressmap::put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)メソッド両方の変換マップを指定しない限り、します。  
  
## <a name="see-also"></a>関連項目  
 [DiaAddressMapEntry 構造体](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap::put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)