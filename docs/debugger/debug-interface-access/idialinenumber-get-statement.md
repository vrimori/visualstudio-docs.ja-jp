---
title: Idialinenumber::get_statement |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b1c2602f9336d5e59a9e692f13170aacf68a1c1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49947934"
---
# <a name="idialinenumbergetstatement"></a>IDiaLineNumber::get_statement
この行の情報がプログラムのソース内の式ではなく、ステートメントの先頭を説明することを示すフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_statement (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`場合、この行の情報には、プログラムのソース内のステートメントの先頭がについて説明します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 ステートメントは、複数の行にまたがることができます。 このメソッドは、関連付けられている行番号が、このような複数行ステートメントの先頭をマークするかどうかを示します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)