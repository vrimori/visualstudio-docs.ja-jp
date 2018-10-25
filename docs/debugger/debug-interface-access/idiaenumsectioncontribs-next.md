---
title: Idiaenumsectioncontribs::next |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSectionContribs::Next method
ms.assetid: a6bb2adb-ee6d-4f3c-ab5b-e89361c8880e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 630914434defea47254597ca0e392379b70a3283
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49818953"
---
# <a name="idiaenumsectioncontribsnext"></a>IDiaEnumSectionContribs::Next
指定した列挙体シーケンス内のセクションの投稿数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Next(   
   ULONG                celt,   
   IDiaSectionContrib** rgelt,  
   ULONG*               pceltFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 celt  
 [in]セクション多大な貢献を取得する列挙子の数。  
  
 rgelt  
 [out]格納する配列、 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)セクションの目的の投稿物を表すオブジェクト。  
  
 pceltFetched  
 [out]列挙子のフェッチにセクションの投稿物の数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`複数セクション投稿がある場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)   
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)