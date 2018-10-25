---
title: Idiastackframe::get_lengthparams |Microsoft Docs
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
- IDiaStackFrame::get_lengthParams method
ms.assetid: 78005efa-2883-4823-b4e4-711a66672c78
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41cc54bdd7961047c807518444a9b386ac025a5b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893535"
---
# <a name="idiastackframegetlengthparams"></a>IDiaStackFrame::get_lengthParams
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

スタックにプッシュするパラメーターのバイト数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_lengthParams (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]パラメーターのバイト数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`プロパティがサポートされていない場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)



