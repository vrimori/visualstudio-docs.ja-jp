---
title: "Idialinenumber::get_columnnumberend |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaLineNumber::get_columnNumberEnd method
ms.assetid: 02fa56c1-87b6-405a-adee-3bb6bc62de2d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 04894f9ef6d1779b5e27c2552b5ea05d84649a2c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idialinenumbergetcolumnnumberend"></a>IDiaLineNumber::get_columnNumberEnd
式またはステートメントが終了するソースの 1 から始まる列数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_columnNumberEnd (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]式またはステートメントの終了列番号を返します。 値がゼロの場合、最後の列情報がありません。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドによって返される列の値は、バイトの行のステートメントの最後の文字後位置に行へのオフセットです。  
  
## <a name="see-also"></a>参照  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)