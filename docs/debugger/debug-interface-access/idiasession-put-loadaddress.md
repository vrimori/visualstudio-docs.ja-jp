---
title: "Idiasession::put_loadaddress |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f4721ee818c4dc75d883c7accd2faa162521de13
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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
  
## <a name="see-also"></a>参照  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)