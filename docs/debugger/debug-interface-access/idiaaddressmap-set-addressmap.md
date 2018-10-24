---
title: Idiaaddressmap::set_addressmap |Microsoft Docs
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
ms.openlocfilehash: 1d097ccbe5c893c603aaa2a018f8fcd422f15ac2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834526"
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
 [in]要素の数、`data`パラメーター。  
  
 `data[]`  
 [in]配列の[DiaAddressMapEntry 構造](../../debugger/debug-interface-access/diaaddressmapentry.md)変換マップを定義する構造体。  
  
 `imagetoSymbols`  
 [in]`TRUE`場合、`data`パラメーター (デバッグ シンボルで説明した) ように新しいイメージのレイアウトから元のレイアウトへのマップを定義します。 `FALSE` 場合`data`元のレイアウトから取得した新しいイメージのレイアウトにマップします。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 通常、DIA は、プログラム データベース (.pdb) ファイルからアドレス変換マップを取得します。 これらの値は、不足している場合、 [idiaaddressmap::set_imageheaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)メソッドは、2 回で 1 回、`imagetoSymbols`パラメーターに設定`TRUE`とに 1 回、`imagetoSymbols`パラメーターに設定`FALSE`します。 使用してマップ、アドレス変換を有効にすることはできません、 [idiaaddressmap::put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)メソッド両方の変換マップを指定しない場合。  
  
## <a name="see-also"></a>関連項目  
 [DiaAddressMapEntry 構造体](../../debugger/debug-interface-access/diaaddressmapentry.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap::put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)   
 [IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)