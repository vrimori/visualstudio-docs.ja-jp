---
title: Idiainjectedsource::get_crc |Microsoft Docs
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
- IDiaInjectedSource::get_crc method
ms.assetid: 2ecdda93-950e-40d6-b79b-4ae3c55b6cfc
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfdf56a7bf776b5dfc6d77ef885191e69a75fc70
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49823204"
---
# <a name="idiainjectedsourcegetcrc"></a>IDiaInjectedSource::get_crc
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ソース コードのバイト数から計算された巡回冗長検査 (CRC) を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_crc (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します、CRC は、ソース コードのバイト数から計算されます。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)



