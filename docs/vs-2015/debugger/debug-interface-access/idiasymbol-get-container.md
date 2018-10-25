---
title: Idiasymbol::get_container |Microsoft Docs
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
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 127c76776285c747de27fa2a277226e541a4e981
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828950"
---
# <a name="idiasymbolgetcontainer"></a>IDiaSymbol::get_container
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

この関数は、この記号の親/コンテナーを表すシンボルへのポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_container(  
   IDiaSymbol **pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]ポインターを返します、`IDiaSymbol`このシンボルのコンテナーに関する情報を格納します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、S_OK を返します。それ以外の場合、S_FALSE またはエラー コードを返します。  
  
> [!NOTE]
>  S_FALSE の戻り値は、プロパティがシンボルを使用できないことを意味します。  
  
## <a name="requirements"></a>必要条件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|Dia2.h|  
|バージョン:|DIA SDK バージョン 8.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



