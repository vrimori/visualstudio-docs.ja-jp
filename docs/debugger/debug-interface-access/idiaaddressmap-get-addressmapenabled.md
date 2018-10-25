---
title: Idiaaddressmap::get_addressmapenabled |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 47d0b3ac64724881ab72cb9d9d873bc02f3bec9b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938839"
---
# <a name="idiaaddressmapgetaddressmapenabled"></a>IDiaAddressMap::get_addressMapEnabled
特定のセッション用アドレス マップに設定されているかどうかを示します。  
  
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
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 場合があります、ポスト プロセッサの実行可能ファイルは、実行可能ファイルを更新します。 DIA には、新しいレイアウトにシンボルの変換をサポートするためのメカニズムが含まれています。  
  
 クライアント アプリケーションは、特定のセッションのアドレス マップを取得することによって設定できます、 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)からインターフェイス、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)インターフェイスと呼び出し、 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)メソッドへの呼び出しに続けて、 [idiaaddressmap::put_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)メソッド。 `get_addressMapEnabled`メソッド呼び出しの結果を返します、`put_addressMapEnabled`メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Idiaaddressmap::set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)