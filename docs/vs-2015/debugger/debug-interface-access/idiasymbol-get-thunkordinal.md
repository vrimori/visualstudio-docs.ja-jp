---
title: Idiasymbol::get_thunkordinal |Microsoft Docs
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
- IDiaSymbol::get_thunkOrdinal method
ms.assetid: 4b28d78a-1974-4d8a-8bb7-781bf630f2f4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 853ac0101ebccd6b6117b4b3635224ebc01c35f1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292124"
---
# <a name="idiasymbolgetthunkordinal"></a>IDiaSymbol::get_thunkOrdinal
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

関数のサンクの型を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_thunkOrdinal (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]値を返します、 [THUNK_ORDINAL 列挙型](../../debugger/debug-interface-access/thunk-ordinal.md)関数のサンクの型を指定する列挙体。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>Remarks  
 このプロパティは有効な場合にのみとしてシンボルを[SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)の値`SymTagThunk`します。  
  
 「サンク」は、32 ビット メモリ アドレス空間 (フラットのアドレス空間とも呼ばれます) と (セグメント化されたアドレス空間と呼ばれます)、16 ビットのアドレス空間を変換するコードです。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [THUNK_ORDINAL 列挙型](../../debugger/debug-interface-access/thunk-ordinal.md)   
 [SymTagEnum 列挙型](../../debugger/debug-interface-access/symtagenum.md)



