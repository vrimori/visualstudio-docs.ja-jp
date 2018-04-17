---
title: IDiaAddressMap |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: 07083ce54496992156103c58c5428cedbd321b83
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiaaddressmap"></a>IDiaAddressMap
DIA SDK が仮想のアドレスと相対仮想アドレス デバッグ オブジェクトを計算する方法の制御を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
IDiaAddressMap : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
 次の表は、メソッドの`IDiaAddressMap`します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)|アドレス マップが特定のセッションの確立されたかどうかを示します。|  
|[IDiaAddressMap::put_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-addressmapenabled.md)|記号のアドレスを変換するアドレス マップを使用するかどうかを指定します。|  
|[IDiaAddressMap::get_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-relativevirtualaddressenabled.md)|計算と相対仮想アドレスの使用が有効かどうかを示します。|  
|[IDiaAddressMap::put_relativeVirtualAddressEnabled](../../debugger/debug-interface-access/idiaaddressmap-put-relativevirtualaddressenabled.md)|クライアントは有効にするにまたは相対仮想アドレスの計算を無効にできます。|  
|[IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)|現在のイメージの配置を取得します。|  
|[IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)|イメージの配置を設定します。|  
|[IDiaAddressMap::set_imageHeaders](../../debugger/debug-interface-access/idiaaddressmap-set-imageheaders.md)|セットのイメージの相対仮想アドレスの変換を有効にするヘッダー。|  
|[IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)|イメージのレイアウトの翻訳をサポートするために、アドレス マップを提供します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスで提供されるコントロールが 2 組の指定したデータにカプセル化: イメージのヘッダーと、マップに対応します。 ほとんどのクライアントを使用して、 [idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)イメージと、メソッド通常がわかるために必要なヘッダーとマップ データ自体のすべての適切なデバッグ情報を検索するメソッド。 ただし一部のクライアントは、特殊な処理とデータの検索を実装します。 このようなクライアントのメソッドを使用して、`IDiaAddressMap`検索結果に DIA SDK を提供するインターフェイスです。  
  
## <a name="notes-for-callers"></a>呼び出し元のノート  
 このインターフェイスを指定する場合は、DIA セッション オブジェクトで実行できます。 クライアントの呼び出し、 `QueryInterface` DIA セッション オブジェクト インターフェイスで、通常メソッド[IDiaSession](../../debugger/debug-interface-access/idiasession.md)、取得するため、`IDiaAddressMap`インターフェイスです。  
  
## <a name="requirements"></a>要件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>関連項目  
 [インターフェイス (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Idiadatasource::loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)