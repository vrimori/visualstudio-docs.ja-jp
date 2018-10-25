---
title: Idiasymbol::get_slot |Microsoft Docs
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
- IDiaSymbol::get_slot method
ms.assetid: 97e405b8-483f-4da0-91e7-ca4d88251ecd
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e97fa7d0ef6fd03c8e3d7ee58e21ae44ca82c89
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922680"
---
# <a name="idiasymbolgetslot"></a>IDiaSymbol::get_slot
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

場所のスロット番号を取得します。 使用する場合、 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)は`LocIsSlot`します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_slot (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]場所のスロット数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティがシンボルを使用できないことを意味します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType 列挙型](../../debugger/debug-interface-access/locationtype.md)



