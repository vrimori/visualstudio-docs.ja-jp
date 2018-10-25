---
title: IDiaEnumSectionContribs::get__NewEnum |Microsoft Docs
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
- IDiaEnumSectionContribs::get__NewEnum method
ms.assetid: a16ee92f-3081-416a-98f6-ce6bc8288a8b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97c737399b789693e8b69366c1972a6039ac8474
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904467"
---
# <a name="idiaenumsectioncontribsgetnewenum"></a>IDiaEnumSectionContribs::get__NewEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)



