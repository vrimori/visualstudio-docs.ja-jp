---
title: Idiasymbol::get_hasmanagedcode |Microsoft Docs
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
- IDiaSymbol::get_hasManagedCode method
ms.assetid: e40f82f5-88fe-4a9b-b594-3605f42773ec
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 719c8b963ccc88a5671699813750d248a474659c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49937046"
---
# <a name="idiasymbolgethasmanagedcode"></a>IDiaSymbol::get_hasManagedCode
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

マネージ コードが、モジュールに含まれるかどうかを示すフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_hasManagedCode(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pFlag`  
 [out]返します`TRUE`モジュールには、マネージ コードが含まれている場合を返しますそれ以外の場合、`FALSE`コードがアンマネージ コード。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティがシンボルを使用できないことを意味します。  
  
## <a name="remarks"></a>Remarks  
 このプロパティは、`SymTagCompilandDetails`記号の型 (を参照してください[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md))。  
  
## <a name="requirements"></a>必要条件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|Dia2.h|  
|バージョン:|DIA SDK バージョン 8.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)



