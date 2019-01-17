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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09ba0e015ae4383a0d8bb215d565635570f04daa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53951447"
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