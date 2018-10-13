---
title: Idiaenumsymbolsbyaddr::symbolbyva |Microsoft Docs
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
- IDiaEnumSymbolsByAddr::symbolByVA method
ms.assetid: ac84339f-70c6-48ed-85d0-6d7d1b5194e8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8bef471e5170cbc376dc26f5fae88ce98e50cbaf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215840"
---
# <a name="idiaenumsymbolsbyaddrsymbolbyva"></a>IDiaEnumSymbolsByAddr::symbolByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

仮想アドレス (VA) で検索を実行して、列挙子を配置します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT symbolByVA (   
   DWORD**      virtualAddress,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 virtualAddress  
 [in]仮想アドレス。  
  
 ppsymbol  
 [out]返します、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)シンボルを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合は、シンボルが見つかりませんでした。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



