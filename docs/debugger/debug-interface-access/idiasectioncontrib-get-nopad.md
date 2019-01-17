---
title: Idiasectioncontrib::get_nopad |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 694925b51d2cb65d4a3e1f38b54c20926b5895c7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910910"
---
# <a name="idiasectioncontribgetnopad"></a>IDiaSectionContrib::get_nopad
[次へ] のメモリ境界にセクションを埋めいないかどうかを示すフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_nopad(  
   BOOL* pRetVal  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`セクションする必要があります。 [次へ] のメモリ境界行われていない場合、それ以外の場合を返します`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 これは通常、古いファイルでのみ見プロパティです。  
  
## <a name="see-also"></a>「  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)