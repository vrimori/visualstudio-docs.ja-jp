---
title: IDiaAddressMap |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap interface
ms.assetid: e6467529-508c-4328-85d7-89444ae4d1c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a563ee3502cc1e713946cd70575be187ecbeadbb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824549"
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
DIA SDK がデバッグ オブジェクトの仮想および相対の仮想アドレスを計算する方法を制御できます。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaAddressMap`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|特定のセッション用アドレス マップに設定されているかどうかを示します。|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|シンボルのアドレスに変換するアドレス マップを使用するかどうかを指定します。|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|計算と相対仮想アドレスの使用が有効かどうかを示します。|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|クライアントは有効または相対仮想アドレスの計算を無効にできます。|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|現在のイメージの配置を取得します。|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|イメージの配置を設定します。|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|イメージの相対仮想アドレス変換を有効にするヘッダーのセット。|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|イメージのレイアウトの翻訳をサポートするために、アドレス マップを提供します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスによって提供されるコントロールは 2 つを指定するデータのセットにカプセル化: イメージのヘッダーと、マップに対応します。 ほとんどのクライアントを使用して、 [idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)イメージと、メソッドことが必要なヘッダーとマップ データ自体のすべてを検出通常の適切なデバッグ情報を検索するメソッド。 ただし一部のクライアントは、特殊な処理とデータの検索を実装します。 このようなクライアントのメソッドを使用して、 `IDiaAddressMap` DIA SDK 検索結果を提供するインターフェイス。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスは、DIA セッション オブジェクトから入手できます。 クライアントの呼び出し、 `QueryInterface` DIA セッション オブジェクト インターフェイスで、通常はメソッド[IDiaSession](../../debugger/debug-interface-access/idiasession.md)、取得、`IDiaAddressMap`インターフェイス。  
  
## <a name="requirements"></a>要件  
 ヘッダー:dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>関連項目
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
