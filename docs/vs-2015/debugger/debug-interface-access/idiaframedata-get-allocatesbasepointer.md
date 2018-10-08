---
title: Idiaframedata::get_allocatesbasepointer |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3259aa3dca2fba1867df11b0b9dea467b7fecf37
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47538472"
---
# <a name="idiaframedatagetallocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[idiaframedata::get_allocatesbasepointer](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer)します。  
  
このアドレスの範囲内のコード ベースのポインターが割り当てられているかどうかを示すフラグを取得します。 このメソッドが非推奨とされます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`基本ポインターが割り当てられている場合を返しますそれ以外の場合、`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このプロパティは FPO_DATA にアクセスしていたをまたはプログラム文字列がによって返されるときにコードからのみ使用する必要があります、 [idiaframedata::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)メソッドは`NULL`します。 それ以外の場合、プログラム文字列には、前のレジスタ値を計算するために必要なすべての情報が含まれています。  
  
## <a name="see-also"></a>関連項目  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)



