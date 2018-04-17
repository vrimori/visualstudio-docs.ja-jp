---
title: Idiasession::put_loadaddress |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fa8f7c12e07f68d8c3fdd85f0d33d964847abf22
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiasessionputloadaddress"></a>IDiaSession::put_loadAddress
このシンボル ストアで、シンボルに対応する実行可能ファイルの読み込みアドレスを設定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `NewVal`  
 [in]実行可能ファイルのアドレスをロードします。  
  
## <a name="remarks"></a>コメント  
 シンボルの仮想アドレス (VA) のプロパティは、このメソッドの値を使用して計算されます。 このプロパティは 0 以外設定されていない限り、仮想のアドレスは計算されません。  
  
> [!NOTE]
>  取得する場合は、このメソッドを呼び出す必要があります、 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)オブジェクトおよびシンボルで任意の仮想プロパティを使用する必要がある場合、オブジェクトの使用を開始する前にします。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)