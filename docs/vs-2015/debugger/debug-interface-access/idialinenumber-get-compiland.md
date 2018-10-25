---
title: Idialinenumber::get_compiland |Microsoft Docs
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
- IDiaLineNumber::get_compiland method
ms.assetid: c476d0b8-c473-47eb-96f5-c4e8f577b1c9
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8267db2077029bd8a428fddad59aacfdd2f0692b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49887229"
---
# <a name="idialinenumbergetcompiland"></a>IDiaLineNumber::get_compiland
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

イメージのテキストのバイト数を提供するコンパイル単位のシンボルへの参照を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_compiland (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 pRetVal  
 [out]返します、 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)イメージのテキストのバイト数を提供するコンパイル単位のオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)



