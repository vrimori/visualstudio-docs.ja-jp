---
title: IDiaSymbol::get_isMatrixRowMajor |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: 36b1e881-ea76-48b0-b67f-e9eb0d19bec7
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fd1486d166554e7b1ecb557f668e99a8797bae0
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176606"
---
# <a name="idiasymbolgetismatrixrowmajor"></a>IDiaSymbol::get_isMatrixRowMajor
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

マトリックスが主要な行であるかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT get_isMatrixRowMajor(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]ポインターを`BOOL`マトリックスに主要な行がかどうかを指定します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



