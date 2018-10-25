---
title: Idiasymbol::get_machinetype |Microsoft Docs
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
- IDiaSymbol::get_machineType method
ms.assetid: 30870b10-6f32-45c6-a0d7-020dea707710
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77f9351b038ac66df64c5d2ca546717b52ec647c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884304"
---
# <a name="idiasymbolgetmachinetype"></a>IDiaSymbol::get_machineType
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ターゲット CPU の種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_machineType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]値を返します、 [CV_CPU_TYPE_e 列挙型](../../debugger/debug-interface-access/cv-cpu-type-e.md)ターゲット CPU の種類を指定する列挙体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="see-also"></a>関連項目  
 [CV_CPU_TYPE_e 列挙型](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



