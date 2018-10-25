---
title: Idiasymbol::get_intrinsic |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_intrinsic method
ms.assetid: f969f595-d9f9-48b9-adaa-63a6e4e09575
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 14f5525a63e4453c594cd84b248f71303b083312
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49931221"
---
# <a name="idiasymbolgetintrinsic"></a>IDiaSymbol::get_intrinsic
クラスは、組み込みの型であるかどうかを指定するフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_intrinsic(   
   BOOL* pRetVal)  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`クラスが、組み込み型の場合を返しますそれ以外の場合、`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)