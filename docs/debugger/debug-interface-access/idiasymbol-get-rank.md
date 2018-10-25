---
title: Idiasymbol::get_rank |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_rank method
ms.assetid: 14cc9c4b-a5ec-414a-b01f-4a142c17b7cc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fc12e9251bd452edc3fdede1a5f7414462162301
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847696"
---
# <a name="idiasymbolgetrank"></a>IDiaSymbol::get_rank
FORTRAN の多次元配列のランク (次元数) を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_rank (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]FORTRAN の多次元配列の次元数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>Remarks  
 ランクとして、配列が宣言されている配列の次元数を指す`myarray[1,2,3]`します。 この例では、3、3 つのディメンションのランクがあります。 ランクは、各次元の配列の配列の概念を使用する C++ には適用されません (つまり、 `myarray[1][2][3]`)。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)