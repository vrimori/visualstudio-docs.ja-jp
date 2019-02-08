---
title: Idiaaddressmap::get_imagealign |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 03f288b0da63e3740a2d954aab2100fa97551154
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936036"
---
# <a name="idiaaddressmapgetimagealign"></a>IDiaAddressMap::get_imageAlign
現在のイメージの配置を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]実行可能ファイルからイメージの配置の値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 イメージは、イメージが読み込まれ、作成する方法に応じて特定のメモリ境界に揃えて配置されます。 配置は、1、2、4、8、16、32、または 64 バイト境界には通常です。 イメージの配置への呼び出しで設定できる、 [idiaaddressmap::put_imagealign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)メソッド。  
  
## <a name="see-also"></a>関連項目
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)
