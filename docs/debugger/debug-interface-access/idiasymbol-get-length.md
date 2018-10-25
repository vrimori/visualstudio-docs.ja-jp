---
title: Idiasymbol::get_length |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_length method
ms.assetid: cc62f028-d195-4fbf-93bc-10b08bef52d2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f99a2012d0c3f009540c988df6e41b0a7d0cf4e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844524"
---
# <a name="idiasymbolgetlength"></a>IDiaSymbol::get_length
この記号によって表されるオブジェクトによって使用されるメモリのバイトまたはビット数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_length (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]この記号によって表されるオブジェクトによって使用されるメモリのビットまたはバイト数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>Remarks  
 場合、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)のシンボルは`LocIsBitField`、このメソッドによって返される文字数は bits では、文字数はそれ以外の場合、その他のすべての場所の種類のバイト数でします。  
  
## <a name="example"></a>例  
  
```C++  
IDiaSymbol* pSymbol;  
ULONGLONG   length;  
pSymbol->get_length( &length );  
```  
  
## <a name="requirements"></a>必要条件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|Dia2.h|  
|バージョン:|DIA SDK v7.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)