---
title: IDiaEnumSymbols::get__NewEnum |Microsoft Docs
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
- IDiaEnumSymbols::get__NewEnum method
ms.assetid: 879609ea-8e5a-4fa3-afa6-d24870fb4392
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66c6c61c521cce9c8a0ffaf8b252334a9e74b85f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547815"
---
# <a name="idiaenumsymbolsgetnewenum"></a>IDiaEnumSymbols::get__NewEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[IDiaEnumSymbols::get__NewEnum](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumsymbols-get-newenum)します。  
  
取得、<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>この列挙子のバージョン。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pRetVal  
 [out]返します、`IUnknown`インターフェイスを表す、<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>この列挙子のバージョン。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)



