---
title: Idiaframedata::get_addresssection |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_addressSection method
ms.assetid: e4eedede-4a1c-4da2-a812-b92df328fd8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fd246ce9f547f72936a899602c439d1afcd05a45
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911435"
---
# <a name="idiaframedatagetaddresssection"></a>IDiaFrameData::get_addressSection
フレームのコード アドレスのセクションの一部を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]フレームのコード アドレスのセクションの一部を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)