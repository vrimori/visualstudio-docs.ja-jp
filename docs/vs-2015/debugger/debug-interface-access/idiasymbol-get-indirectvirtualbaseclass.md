---
title: Idiasymbol::get_indirectvirtualbaseclass |Microsoft Docs
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
- IDiaSymbol::get_indirectVirtualBaseClass method
ms.assetid: 853b5c6f-e1cb-4675-ad36-9ee16e3341c3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fa1331e546d199ff0a99d71b72f9e420eaccc69
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911539"
---
# <a name="idiasymbolgetindirectvirtualbaseclass"></a>IDiaSymbol::get_indirectVirtualBaseClass
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ユーザー定義データ型が間接仮想基底クラスであるかどうかを指定するフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_indirectVirtualBaseClass (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`場合; の間接仮想基底クラスは、ユーザー定義データ型を返しますそれ以外の場合、`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティが、シンボルの使用可能なことを意味します。  
  
## <a name="requirements"></a>必要条件  
  
|必要条件|説明|  
|-----------------|-----------------|  
|ヘッダー:|Dia2.h|  
|バージョン:|DIA SDK v7.0|  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



