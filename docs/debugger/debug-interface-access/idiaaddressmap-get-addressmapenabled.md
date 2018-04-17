---
title: Idiaaddressmap::get_addressmapenabled |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_addressMapEnabled method
ms.assetid: 6183dc5e-befa-4e5a-ae5a-f4aa24f3ed9e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 225cac39cb56bbf5b03478c6009162c711baad87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
アドレス マップが特定のセッションの確立されたかどうかを示します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_addressMapEnabled (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pRetVal  
 [out]返します`TRUE`アドレスのマッピングが有効になっている場合。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 場合があります、ポスト プロセッサの実行可能ファイルは、実行可能ファイルを更新します。 DIA には、新しいレイアウトにシンボルの変換をサポートするためのメカニズムが含まれています。  
  
 クライアント アプリケーションは、特定のセッションのアドレス マップを取得することによって設定できます、 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)からインターフェイス、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)インターフェイスと呼び出し元、 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)メソッドへの呼び出しに続けて、 [idiaaddressmap::put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)メソッドです。 `get_addressMapEnabled`メソッド呼び出しの結果を返します、`put_addressMapEnabled`メソッドです。  
  
## <a name="see-also"></a>関連項目  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaaddressmap::set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)