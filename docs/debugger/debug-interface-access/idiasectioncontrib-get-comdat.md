---
title: Idiasectioncontrib::get_comdat |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a15e0001342a31d13cb1b77f2c8e6d7fc4d31c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936269"
---
# <a name="idiasectioncontribgetcomdat"></a>IDiaSectionContrib::get_comdat
セクションは COMDAT レコードであるかどうかを示すフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_comdat (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`セクションが COMDAT レコード以外の場合を返しますそれ以外の場合、`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 COMDAT レコードとは、パッケージ化された関数をリンカーに表示する一般的なオブジェクト ファイル形式 (COFF) レコードです。  
  
## <a name="see-also"></a>「  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)