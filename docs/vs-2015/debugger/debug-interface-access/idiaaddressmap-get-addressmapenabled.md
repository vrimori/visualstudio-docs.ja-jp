---
title: Idiaaddressmap::get_addressmapenabled |Microsoft Docs
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
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 59a3ded58dcec258acdc9620f92ae6a9c653bff7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754107"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

特定のセッション用アドレス マップに設定されているかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pRetVal  
 [out]返します`TRUE`アドレスのマッピングが有効になっている場合。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 場合があります、ポスト プロセッサの実行可能ファイルは、実行可能ファイルを更新します。 DIA には、新しいレイアウトにシンボルの変換をサポートするためのメカニズムが含まれています。  
  
 クライアント アプリケーションは、特定のセッションのアドレス マップを取得することによって設定できます、 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)からインターフェイス、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)インターフェイスと呼び出し、 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)メソッドへの呼び出しに続けて、 [idiaaddressmap::put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)メソッド。 `get_addressMapEnabled`メソッド呼び出しの結果を返します、`put_addressMapEnabled`メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaaddressmap::set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)



