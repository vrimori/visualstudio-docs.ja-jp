---
title: Idiasymbol::get_nostackordering |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noStackOrdering method
ms.assetid: a1753917-705b-4165-9880-d05e91e6dcb4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82f0b0b25c90a4cba2de6fb45164d9a6bf77446c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49884239"
---
# <a name="idiasymbolgetnostackordering"></a>IDiaSymbol::get_noStackOrdering
この関数は、スタックの順序付けでしたを実行できるかないスタック バッファーのチェックの一部としてを示すフラグを取得します。 ([/GS (バッファー セキュリティ チェック)](/cpp/build/reference/gs-buffer-security-check)コンパイラ オプション)。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_noStackOrdering(  
   BOOL *pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`返しますそれ以外の場合、スタックの順序付けでしたが行われない場合スタック バッファーのチェックがの一部として`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティがシンボルを使用できないことを意味します。  
  
## <a name="requirements"></a>必要条件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|Dia2.h|  
|バージョン:|DIA SDK バージョン 8.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [/GS (バッファーのセキュリティ チェック)](/cpp/build/reference/gs-buffer-security-check)