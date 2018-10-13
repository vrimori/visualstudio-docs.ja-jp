---
title: Idiasectioncontrib::get_execute |Microsoft Docs
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
- IDiaSectionContrib::get_execute method
ms.assetid: 66eb38ce-a5e1-467e-b845-b3dc433eda91
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e566514b5c8f448ffbd90ee5206a9f68b772b883
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49205459"
---
# <a name="idiasectioncontribgetexecute"></a>IDiaSectionContrib::get_execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

セクションがコードとして実行可能かどうかを示すフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_excute (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`セクションをコードとして実行できる場合を返しますそれ以外の場合、`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



