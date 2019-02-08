---
title: Idiaaddressmap::set_imageheaders |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6593092fc155a375480f082a1f82dc53a1d851fa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834140"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
イメージの相対仮想アドレス変換を有効にするヘッダーのセット。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 cbData  
 [in]ヘッダーのデータのバイト数。 必要があります`n*sizeof(IMAGE_SECTION_HEADER)`場所`n`実行可能ファイル内のセクション ヘッダーの数です。  
  
 data[]  
 [in]配列の`IMAGE_SECTION_HEADER`イメージ ヘッダーとして使用する構造体。  
  
 originalHeaders  
 [in]設定`FALSE`イメージ ヘッダーが、新しいイメージである場合`TRUE`アップグレードの前に、元のイメージが反映される場合。 通常、この設定`TRUE`への呼び出しとの組み合わせでのみ、 [idiaaddressmap::set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)メソッド。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 `IMAGE_SECTION_HEADER`構造は、Winnt.h で宣言されているし、実行可能ファイルのイメージ セクション ヘッダーの形式を表します。  
  
 相対仮想アドレスの計算によって異なります、`IMAGE_SECTION_HEADER`値。 通常、DIA では、これらのプログラム データベース (.pdb) ファイルから取得します。 これらの値が存在しない場合、DIA を相対仮想アドレスを計算することは、 [idiaaddressmap::get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)メソッドを返します。`FALSE`します。 クライアントが呼び出す必要がありますし、 [idiaaddressmap::put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)イメージ自体から不足しているイメージ ヘッダーを指定したら、相対仮想アドレスの計算を有効にするメソッド。  
  
## <a name="see-also"></a>関連項目
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)
