---
title: IDiaTable::get__NewEnum |Microsoft Docs
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
- IDiaTable::get__NewEnum method
ms.assetid: ee89bba8-5d5c-4a0b-aa0d-1aad56baa380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0de88aeb8f28b31554782ec820790b23722e4c7a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547613"
---
# <a name="idiatablegetnewenum"></a>IDiaTable::get__NewEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDiaTable::get__NewEnum](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiatable-get-newenum)します。  
  
取得、<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>この列挙子のバージョン。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します、`IUnknown`インターフェイスを表す、<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>この列挙子のバージョン。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)



