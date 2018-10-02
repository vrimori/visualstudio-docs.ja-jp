---
title: IDiaSymbol::get_numberOfRows |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: cf3eb110-d07f-4995-b68b-08290aa67d6f
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd0e41adcafa17b4040113c6c3382e3392ea905c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47548428"
---
# <a name="idiasymbolgetnumberofrows"></a>IDiaSymbol::get_numberOfRows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDiaSymbol::get_numberOfRows](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-numberofrows)します。  
  
マトリックス内の行の数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT get_numberOfRows(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]ポインターを`DWORD`マトリックスの行の数を保持しています。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



