---
title: Idialoadcallback 2::restrictoriginalpathaccess |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: dd3cd1f4989e88c41039328cdc4d54071ff49bac
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31458935"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
かどうかが元のデバッグ ディレクトリに .pdb ファイルを検索するかを決定します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 すべてのコード以外のリターン`S_OK`により、元のデバッグ ディレクトリに .pdb ファイルを検索します。 元のデバッグ ディレクトリは、デバッグがオンにすると、実行可能ファイルにコンパイル シンボル ファイルへのパスです。 このパスは必ずしも実行可能ファイルが存在するパスと同じです。  
  
## <a name="see-also"></a>関連項目  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)