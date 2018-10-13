---
title: Idiaaddressmap::put_addressmapenabled |Microsoft Docs
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
- IDiaAddressMap::put_addressMapEnabled method
ms.assetid: 0f205337-4e59-4383-8059-7b1d207d6dcd
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24098d21644b51c134aa7ea20d2ee6efd6d7e814
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193571"
---
# <a name="idiaaddressmapputaddressmapenabled"></a>IDiaAddressMap::put_addressMapEnabled
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

シンボルのアドレスに変換するアドレス マップを使用するかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT put_addressMapEnabled (   
   BOOL NewVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 NewVal  
 [in]設定`TRUE`、記号の翻訳を有効にするか、`FALSE`を無効にします。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 場合があります、ポスト プロセッサの実行可能ファイルは、実行可能ファイルを更新します。 DIA には、新しいレイアウトにシンボルの変換をサポートするためのメカニズムが含まれています。  
  
 PDB ファイルが読み込まれるときに、ファイルに格納されているアドレス マップが有効にします。 ただし、クライアント アプリケーションが呼び出すことによって、独自のアドレス マップを指定する必要がありますが、 [idiaaddressmap::set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)メソッド。 場合、`set_addressMap`メソッドが成功すると、クライアント アプリケーションを呼び出す必要があります、`put_addressMapEnabled`メソッドを`NewVal`パラメーターの`TRUE`アドレスにマップの使用を有効にします。  
  
 呼び出しでアドレス マップを有効になっているは、現在の状態を取得することができます、 [idiaaddressmap::get_addressmapenabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [Idiaaddressmap::set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)   
 [IDiaAddressMap::get_addressMapEnabled](../../debugger/debug-interface-access/idiaaddressmap-get-addressmapenabled.md)



