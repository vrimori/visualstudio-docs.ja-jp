---
title: Idiastackframe::get_lengthsavedregisters |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthSavedRegisters method
ms.assetid: b75fad6e-1ef4-44e6-89e3-c31c6fba10b3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d21eed3ee45ea7b9459f76c4ec17bbd84023b53
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31461741"
---
# <a name="idiastackframegetlengthsavedregisters"></a>IDiaStackFrame::get_lengthSavedRegisters
スタックにプッシュされる保存されたレジスタのバイト数を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_lengthSavedRegisters (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]保存されたレジスタのバイト数を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`プロパティがサポートされていない場合。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)