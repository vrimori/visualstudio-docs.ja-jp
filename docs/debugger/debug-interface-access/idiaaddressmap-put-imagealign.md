---
title: Idiaaddressmap::put_imagealign |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 06110568e0854692b19c3c118e948024bd346295
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903999"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
イメージの配置を設定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 NewVal  
 [in]実行可能ファイルの新しいイメージの配置の値。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 イメージ (読み込まれて実行可能ファイル) は、指定されたメモリ境界に揃えて配置されます。 この配置は、コンパイルとリンク時のオプションと現在のシステム アーキテクチャによって、影響を受けることができます。 イメージの配置は、バイト境界には常にします。 次のイメージの配置の値が無効です: 1、2、4、8、16、32、および 64 バイトの境界。  
  
 現在のイメージの配置への呼び出しで取得できる、 [idiaaddressmap::get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)メソッド。  
  
> [!NOTE]
>  このメソッドを呼び出すことが時間によっては、イメージが既に読み込まれて。 `put_imageAlign`メソッドは通常新しい配置が必要ですし、イメージを移動または変更されている場合に使用します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)