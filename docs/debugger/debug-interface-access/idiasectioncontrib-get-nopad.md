---
title: Idiasectioncontrib::get_nopad |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 0cd7069b9b84ba088c7a40255a8805fc8bb2c394
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49858044"
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
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 これは通常、古いファイルでのみ見プロパティです。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)