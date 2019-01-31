---
title: Idialinenumber::get_columnnumberend |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a528201d7f3ba817da9e903abf4bc7570351711a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919448"
---
# <a name="idialinenumbergetcolumnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
式またはステートメントの終了位置となる 1 ベースのソース列番号を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]式またはステートメントの終了列番号を返します。 値が 0 の場合は、最後の列情報が存在しません。  
  
## <a name="return-value"></a>戻り値  
 正常に終了した場合は、`S_OK` を返します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドによって返される列の値は、バイトの行にステートメントの最後の文字の後の位置に行のオフセットです。  
  
## <a name="see-also"></a>「  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)