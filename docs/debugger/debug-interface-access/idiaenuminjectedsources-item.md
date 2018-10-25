---
title: Idiaenuminjectedsources::item |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Item method
ms.assetid: 14846955-7270-451d-91d2-9cb34bb65187
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8299bce906c5f3e7a38296a9c19e9c85d03501b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917454"
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
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)   
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)