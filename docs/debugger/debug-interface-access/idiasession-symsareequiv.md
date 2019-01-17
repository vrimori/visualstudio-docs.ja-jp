---
title: Idiasession::symsareequiv |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfde8fec8ce399df765c911aa1ffaf292be1e50f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893472"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
2 つのシンボルが等しいかどうかを確認します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT symsAreEquiv (   
   IDiaSymbol* symbolA,  
   IDiaSymbol* symbolB  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `symbolA`  
 [in]最初の[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)比較に使用されるオブジェクト。  
  
 `symbolB`  
 [in]2 番目の`IDiaSymbol`比較に使用されるオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 シンボルと同じ場合を返します`S_OK`。 それ以外を返します`S_FALSE`、シンボルが同じではありません。 それ以外の場合、エラー コードを返します。  
  
## <a name="see-also"></a>「  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)