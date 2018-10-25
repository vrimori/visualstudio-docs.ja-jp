---
title: Idiasymbol::get_value |Microsoft Docs
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
- IDiaSymbol::get_value method
ms.assetid: 2e40174a-2a61-4e5f-bb32-9e0ceec2178a
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 278e199400fa46782035ec767e65f72040d47c4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870225"
---
# <a name="idiasymbolgetvalue"></a>IDiaSymbol::get_value
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

定数の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_value (   
   VARIANT* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [入力、出力]A`VARIANT`オブジェクトを定数の値が入力されます。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドに渡される前に、指定されたバリアントを初期化する必要があります。 詳細については、例を参照してください。  
  
## <a name="example"></a>例  
  
```cpp#  
void ProcessValue(IDiaSymbol *pSymbol)  
{  
    VARIANT value;  
    value.vt = VT_EMPTY;    // Initialize variant for use.  
    if (pSymbol->get_value(&value) == S_OK)  
    {  
        // Do something with value.  
    }  
}  
  
//----------------------------------------------------  
// Alternate approach  
void ProcessValue2(IDiaSymbol *pSymbol)  
{  
    CComVariant value;  
    if (pSymbol->get_value(&value) == S_OK)  
    {  
        // Do something with value  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



