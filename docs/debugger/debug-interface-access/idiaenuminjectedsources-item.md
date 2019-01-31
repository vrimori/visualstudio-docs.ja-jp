---
title: Idiaenuminjectedsources::item |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d258e2c1ba71ab294435f2437c7b6dc3de75cfb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925790"
---
# <a name="idiaenuminjectedsourcesitem"></a>IDiaEnumInjectedSources::Item
インデックスを使用して、挿入されたソースを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaInjectedSource** injectedSource  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 インデックス  
 [in]インデックス、 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)を取得するオブジェクト。 インデックスが範囲 0 `count`-1 の場合、`count`によって返される、 [idiaenuminjectedsources::get_count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)メソッド。  
  
 injectedSource  
 [out]返します、 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)挿入されたソースを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)