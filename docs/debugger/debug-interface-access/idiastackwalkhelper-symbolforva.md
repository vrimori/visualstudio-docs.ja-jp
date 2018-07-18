---
title: Idiastackwalkhelper::symbolforva |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::symbolForVA method
ms.assetid: 8dd9455d-d44c-4dd6-a0aa-31131cbea2aa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0e70dac639f18f934bb997cc4979bdbe6a7d8c4c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31467538"
---
# <a name="idiastackwalkhelpersymbolforva"></a>IDiaStackWalkHelper::symbolForVA
指定した仮想アドレスを含んでいるシンボルを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT symbolForVA(   
   ULONGLONG     va,  
   IDiaSymbol**  ppSymbol  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `va`  
 [in]要求されたシンボルに含まれている仮想アドレス。 シンボルがある必要があります、 `SymTagFunctionType` (から値、 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)列挙型)。  
  
 `ppSymbol`  
 [out][IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)を指定したアドレスにシンボルを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)