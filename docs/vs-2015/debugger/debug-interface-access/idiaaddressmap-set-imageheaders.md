---
title: Idiaaddressmap::set_imageheaders |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::set_imageHeaders method
ms.assetid: a46b9d0e-43e6-433f-b2c7-aa203981e4e4
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3e2504030d3e8f28c1a41dea1c053c7e1deb1bf
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810239"
---
# <a name="idiaaddressmapsetimageheaders"></a>IDiaAddressMap::set_imageHeaders
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

イメージの相対仮想アドレス変換を有効にするヘッダーのセット。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT set_imageHeaders (   
   DWORD cbData,  
   BYTE  data[],  
   BOOL  originalHeaders  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 cbData  
 [in]ヘッダーのデータのバイト数。 必要があります`n*sizeof(IMAGE_SECTION_HEADER)`場所`n`実行可能ファイル内のセクション ヘッダーの数です。  
  
 データ  
 [in]配列の`IMAGE_SECTION_HEADER`イメージ ヘッダーとして使用する構造体。  
  
 originalHeaders  
 [in]設定`FALSE`イメージ ヘッダーが、新しいイメージである場合`TRUE`アップグレードの前に、元のイメージが反映される場合。 通常、この設定`TRUE`への呼び出しとの組み合わせでのみ、 [idiaaddressmap::set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)メソッド。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 `IMAGE_SECTION_HEADER`構造は、Winnt.h で宣言されているし、実行可能ファイルのイメージ セクション ヘッダーの形式を表します。  
  
 相対仮想アドレスの計算によって異なります、`IMAGE_SECTION_HEADER`値。 通常、DIA では、これらのプログラム データベース (.pdb) ファイルから取得します。 これらの値が存在しない場合、DIA を相対仮想アドレスを計算することは、 [idiaaddressmap::get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)メソッドを返します。`FALSE`します。 クライアントが呼び出す必要がありますし、 [idiaaddressmap::put_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)イメージ自体から不足しているイメージ ヘッダーを指定したら、相対仮想アドレスの計算を有効にするメソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap::set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [Idiaaddressmap::get_relativevirtualaddressenabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)   
 [IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)



