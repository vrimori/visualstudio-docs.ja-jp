---
title: Idiaaddressmap::put_imagealign |Microsoft ドキュメント
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
ms.openlocfilehash: e1c87592dc04c244e394f1df06cfa46d77f595a1
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31457726"
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
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 イメージ (読み込まれて実行可能ファイル) は、指定されたメモリ境界に配置されます。 この配置は、コンパイル、リンク時のオプションと現在のシステム アーキテクチャによって、影響を受けることができます。 イメージの配置は、バイト境界には常にします。 次のイメージの配置の値は有効では: 1、2、4、8、16、32、および 64 バイトの境界。  
  
 現在のイメージの配置への呼び出しで取得できる、 [idiaaddressmap::get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)メソッドです。  
  
> [!NOTE]
>  イメージは、このメソッドを呼び出すことができる時間によって既に読み込まれています。 `put_imageAlign`メソッドは、新しい配置が必要と画像が移動または変更されたときに通常使用されます。  
  
## <a name="see-also"></a>関連項目  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)