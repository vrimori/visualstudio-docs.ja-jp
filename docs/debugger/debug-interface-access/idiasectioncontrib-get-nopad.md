---
title: Idiasectioncontrib::get_nopad |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b26005e6e7062fcf5a3a6f0a9aba4ac7a79b92f7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31461016"
---
# <a name="idiasectioncontribgetnopad"></a>IDiaSectionContrib::get_nopad
セクションを次のメモリ境界に埋め込まれませんかどうかを示すフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_nopad(  
   BOOL* pRetVal  
};  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します`TRUE`セクションは次のメモリの境界です。 埋め込まれていません場合、それ以外の場合を返します`FALSE`です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 これは、通常古いファイルにのみ表示されるプロパティです。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)