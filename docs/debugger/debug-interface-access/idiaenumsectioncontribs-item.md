---
title: Idiaenumsectioncontribs::item |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Item method
ms.assetid: 63a28f23-0ca0-44a7-b11b-ca0206d642a0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 00b60f0915ca4e9a4f56cabca05122a5cdebbd6d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468113"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
インデックスを使用してセクション貢献度を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 インデックス  
 [in]インデックス、 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)を取得するオブジェクト。 インデックスが範囲 0 `count`-1 で、ここで`count`によって返される、 [idiaenumsectioncontribs::get_count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)メソッドです。  
  
 section  
 [out]返します、 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)目的セクションの貢献を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [Idiaenumsectioncontribs::get_count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)