---
title: IDiaSymbol::get_liveRangeLength |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_liveRangeLength
ms.assetid: ffcce3cc-085c-44eb-8145-46e3819c54f9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 23a24a4d88e181a447b5228080ae89b8853060ee
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880053"
---
# <a name="idiasymbolgetliverangelength"></a>IDiaSymbol::get_liveRangeLength
ローカル シンボルの有効なアドレスの範囲の長さを返します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_liveRangeLength (   
   ULONGLONG* length  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `length`  
 [out]アドレスの範囲の長さを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
> [!NOTE]
>  返されたエラー コードは、シンボルにライブの範囲の情報がないことを意味します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)