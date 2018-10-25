---
title: Idiasession::symsareequiv |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: bdaa1ab070b6d95af0f28f5bdaa005b9ac808766
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850985"
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
  
## <a name="see-also"></a>関連項目  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)