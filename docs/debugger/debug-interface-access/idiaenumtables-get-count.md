---
title: Idiaenumtables::get_count |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::get_Count method
ms.assetid: 30fa316b-a746-4028-acae-4efcd2066f38
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f92c860cf0b9d99f5fd4b3f08516afb5ddb0373e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960431"
---
# <a name="idiaenumtablesgetcount"></a>IDiaEnumTables::get_Count
テーブルの数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_Count (    LONG* pRetVal  
);  
  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]テーブルの数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)