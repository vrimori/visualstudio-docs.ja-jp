---
title: Idialinenumber::get_sourcefile |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_sourceFile method
ms.assetid: 86fc4411-375e-4b99-8f96-4da2c3f68190
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8833d1a5ccc39cac70cef6995a4e9a5c1bf99125
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31459611"
---
# <a name="idialinenumbergetsourcefile"></a>IDiaLineNumber::get_sourceFile
ソース ファイルへの参照を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_sourceFile (   
   IDiaSourceFile** pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]返します、 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)ソース ファイルを表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`です。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)