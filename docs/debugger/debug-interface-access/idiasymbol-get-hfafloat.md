---
title: "Idiasymbol::get_hfafloat |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_hfaFloat method
ms.assetid: 73ddcffe-cdac-4b03-be42-82ef985d17ee
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 3c849f733bc0bd404923412d9730bbff6e2ba3f1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgethfafloat"></a>IDiaSymbol::get_hfaFloat
ユーザー定義型 (UDT) が同種浮動小数点 (HFA) の集計データは float 型を含むかどうかを指定するフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_hfaFloat(   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`UDT には、float 型; HFA データが含まれている場合を返しますそれ以外の場合、`FALSE`です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値の`S_FALSE`プロパティは、シンボルの使用可能なことを意味します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: Dia2.h  
  
 ライブラリ: diaguids.lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>参照  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)