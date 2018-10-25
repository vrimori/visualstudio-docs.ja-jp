---
title: Idiaenumsectioncontribs::item |Microsoft Docs
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
ms.openlocfilehash: adbba44ed860c825d1e0baac417bc91e0b33e703
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49901932"
---
# <a name="idiaenumsectioncontribsitem"></a>IDiaEnumSectionContribs::Item
インデックスを使用して、セクションの投稿を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Item (   
   DWORD                index,  
   IDiaSectionContrib** section  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 インデックス  
 [in]インデックス、 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)を取得するオブジェクト。 インデックスは 0 ~ の範囲内で、 `count`-1 の場合、`count`によって返される、 [idiaenumsectioncontribs::get_count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)メソッド。  
  
 section  
 [out]返します、 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)店が貢献したセクションの目的を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [Idiaenumsectioncontribs::get_count](../../debugger/debug-interface-access/idiaenumsectioncontribs-get-count.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)