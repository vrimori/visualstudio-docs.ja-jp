---
title: Idiasymbol::get_machinetype |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_machineType method
ms.assetid: 30870b10-6f32-45c6-a0d7-020dea707710
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 71fbb3c4e60241435813fc77aa58ac47ccfd631b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiasymbolgetmachinetype"></a>IDiaSymbol::get_machineType
ターゲット CPU の種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_machineType (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]値を返します、 [CV_CPU_TYPE_e 列挙型](../../debugger/debug-interface-access/cv-cpu-type-e.md)ターゲット CPU の種類を指定する列挙です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値の`S_FALSE`プロパティは、シンボルの使用可能なことを意味します。  
  
## <a name="see-also"></a>関連項目  
 [CV_CPU_TYPE_e 列挙型](../../debugger/debug-interface-access/cv-cpu-type-e.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)