---
title: IDiaSymbol::get_isSdl |Microsoft Docs
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
ms.assetid: 6aa0e116-da75-4643-a4d7-d8e142231e21
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de68705fdf5c97bb7445852d654fee905d1087ed
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539744"
---
# <a name="idiasymbolgetissdl"></a>IDiaSymbol::get_isSdl
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDiaSymbol::get_isSdl](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiasymbol-get-issdl)します。  
  
/SDL オプションを使用して、モジュールをコンパイルするかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT get_isSdl(  
   BOOL *pRetVal);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]ポインターを`BOOL`/SDL オプションを使用して、モジュールをコンパイルするかどうかを指定します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



