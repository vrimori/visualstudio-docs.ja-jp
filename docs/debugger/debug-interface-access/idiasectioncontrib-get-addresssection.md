---
title: Idiasectioncontrib::get_addresssection |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_addressSection method
ms.assetid: 13fe7e0b-c978-4a1d-bb57-64c8583b5e14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 059f3b2ec1510df1d060252512baf38a3484321c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924679"
---
# <a name="idiasectioncontribgetaddresssection"></a>IDiaSectionContrib::get_addressSection
投稿物のアドレスのセクションの一部を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]投稿物のアドレスのセクションの一部を返します。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)