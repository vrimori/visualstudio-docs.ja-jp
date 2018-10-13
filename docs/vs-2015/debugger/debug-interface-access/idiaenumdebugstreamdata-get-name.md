---
title: Idiaenumdebugstreamdata::get_name |Microsoft Docs
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
- IDiaEnumDebugStreamData::get_Name method
ms.assetid: e6cf2bed-ee2b-4122-886d-c20d93df7ff2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f19d23ac4fed14e9c9f9c0a2f461719f522c44ad
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49307587"
---
# <a name="idiaenumdebugstreamdatagetname"></a>IDiaEnumDebugStreamData::get_name
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

デバッグのデータ ストリームの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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



