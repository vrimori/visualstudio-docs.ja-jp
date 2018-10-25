---
title: Idiasymbol::get_locationtype |Microsoft Docs
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
- IDiaSymbol::get_locationType method
ms.assetid: fbb09c43-ebb7-4b4f-be53-ccff86eb183a
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b404f0c70649edfa7853e462711968c0026e1f45
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49835788"
---
# <a name="idiasymbolgetlocationtype"></a>IDiaSymbol::get_locationType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

データ シンボルの場所の種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_locationType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]値を返します、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)などのデータのシンボルの場所の種類を指定する列挙体`static`または`local`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)



