---
title: Idialoadcallback 2::restrictoriginalpathaccess |Microsoft Docs
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
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7ebea1841a5d546bf30de7a900abf5278b98067
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49265305"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

元のデバッグ ディレクトリに .pdb ファイルを検索する問題であるかを決定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT RestrictOriginalPathAccess ();  
```  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 すべてのコード以外のリターン`S_OK`元のデバッグ ディレクトリに .pdb ファイルを検索できないようにします。 元のデバッグ ディレクトリは、デバッグがオンにすると、実行可能ファイルにコンパイル シンボル ファイルへのパスです。 このパスが必ずしも同じ実行可能ファイルが存在するパスです。  
  
## <a name="see-also"></a>関連項目  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)



