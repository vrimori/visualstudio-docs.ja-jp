---
title: Idiasymbol::get_pure |Microsoft Docs
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
helpviewer_keywords:
- IDiaSymbol::get_pure method
ms.assetid: b61107e9-9144-4981-b7ef-58a339b80c58
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dcc8d67a426008d040f4c80b28f6fcd07fb2092e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232356"
---
# <a name="idiasymbolgetpure"></a>IDiaSymbol::get_pure
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

関数が純粋なかどうかを指定するフラグを取得します。 仮想です。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_pure (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`関数が純粋な場合。 それ以外の場合、返します`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



