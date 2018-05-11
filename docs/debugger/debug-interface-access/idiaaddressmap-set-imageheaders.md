---
title: Idiaaddressmap::set_imageheaders |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 51b68475b9ef0374f95febabc2997524bfd61259
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
セットのイメージの相対仮想アドレス変換を有効にするヘッダー。  
  
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
 [in]ヘッダーのデータのバイト数。 必要があります`n*sizeof(IMAGE_SECTION_HEADER)`場所`n`実行可能ファイルでセクション ヘッダーの数です。  
  
 データ  
 [in]配列`IMAGE_SECTION_HEADER`イメージ ヘッダーとして使用する構造体。  
  
 originalHeaders  
 [in]設定`FALSE`イメージ ヘッダーから返される場合、新しいイメージ`TRUE`アップグレードする前に、元のイメージが反映される場合。 通常、これに設定する`TRUE`への呼び出しとの組み合わせでのみ、 [idiaaddressmap::set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)メソッドです。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 `IMAGE_SECTION_HEADER`構造は、Winnt.h で宣言されているし、実行可能ファイルのイメージ セクション ヘッダーの形式を表します。  
  
 相対仮想アドレスの計算によって異なります、`IMAGE_SECTION_HEADER`値。 通常、DIA では、これらのプログラム データベース (.pdb) ファイルから取得します。 これらの値が存在しない、DIA ができない場合は相対仮想アドレスを計算して、 [idiaaddressmap::get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)メソッドを返します。`FALSE`です。 クライアントが呼び出す必要がありますし、 [idiaaddressmap::put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)メソッドを提供すると、不足しているイメージからヘッダー イメージ自体の相対仮想アドレス計算を有効にします。  
  
## <a name="see-also"></a>関連項目  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap::set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [Idiaaddressmap::get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)