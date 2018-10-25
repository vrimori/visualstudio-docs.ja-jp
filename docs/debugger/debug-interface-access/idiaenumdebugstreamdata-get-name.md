---
title: Idiaenumdebugstreamdata::get_name |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::get_Name method
ms.assetid: e6cf2bed-ee2b-4122-886d-c20d93df7ff2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 247ad261d25cfd0624a5c1d02c17149c9a6a9c6d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49902920"
---
# <a name="idiaenumdebugstreamdatagetname"></a>IDiaEnumDebugStreamData::get_name
デバッグのデータ ストリームの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_Name (   
   BSTR * pRetVal  
)  
```  
  
#### <a name="parameters"></a>パラメーター  
 pRetVal  
 [out]デバッグのデータ ストリームの名前を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)