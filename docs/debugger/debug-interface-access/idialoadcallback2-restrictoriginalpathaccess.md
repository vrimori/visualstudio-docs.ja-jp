---
title: Idialoadcallback 2::restrictoriginalpathaccess |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b88ea861c34eef8761b22cdc4c23f4e79a6b978
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872301"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
元のデバッグ ディレクトリに .pdb ファイルを検索する問題であるかを決定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 すべてのコード以外のリターン`S_OK`元のデバッグ ディレクトリに .pdb ファイルを検索できないようにします。 元のデバッグ ディレクトリは、デバッグがオンにすると、実行可能ファイルにコンパイル シンボル ファイルへのパスです。 このパスが必ずしも同じ実行可能ファイルが存在するパスです。  
  
## <a name="see-also"></a>「  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)