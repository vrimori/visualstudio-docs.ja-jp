---
title: Idiasymbol::get_timestamp |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_timeStamp method
ms.assetid: 5d707b76-dbaa-4d88-86c3-6f3672cc6d4c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 94150440d3fa94e8a511b62d053be01fd39ed6c0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49873098"
---
# <a name="idiasymbolgettimestamp"></a>IDiaSymbol::get_timeStamp
基になる実行可能ファイルのタイムスタンプを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_timeStamp (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]基になる実行可能ファイルのタイムスタンプを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)