---
title: Idiaframedata::get_allocatesbasepointer |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fdeab20ee39dc62688f7cf4604e00117d9eb676f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idiaframedatagetallocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
このアドレスの範囲内のコード ベースのポインターが割り当てられているかどうかを示すフラグを取得します。 このメソッドは推奨されません。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`基本ポインターが割り当てられている場合を返しますそれ以外の場合、`FALSE`です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このプロパティは FPO_DATA にアクセスしていたこと、またはプログラム文字列がによって返されるときにコードでのみ使用する必要があります、 [idiaframedata::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)メソッドは`NULL`します。 それ以外の場合、プログラムの文字列には、以前の登録値を計算するために必要なすべての情報が含まれています。  
  
## <a name="see-also"></a>関連項目  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)