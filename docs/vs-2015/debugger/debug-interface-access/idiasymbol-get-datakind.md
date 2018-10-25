---
title: Idiasymbol::get_datakind |Microsoft Docs
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
- IDiaSymbol::get_dataKind method
ms.assetid: 45005ad0-8b29-4cde-9d33-6bef72f6e463
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f118d3a7b2e9e7c1c0051b16b4ec035c62e728c1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928569"
---
# <a name="idiasymbolgetdatakind"></a>IDiaSymbol::get_dataKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

データ シンボルの変数の分類を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_dataKind (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]値を返します、 [DataKind 列挙型](../../debugger/debug-interface-access/datakind.md)など、グローバル、静的、または定数などのデータの種類を指定する列挙体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティがシンボルを使用できないことを意味します。  
  
## <a name="requirements"></a>必要条件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|Dia2.h|  
|バージョン:|DIA SDK v7.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [DataKind 列挙型](../../debugger/debug-interface-access/datakind.md)



