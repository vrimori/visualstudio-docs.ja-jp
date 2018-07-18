---
title: Idiaenuminjectedsources::clone |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources::Clone method
ms.assetid: 18038691-c140-426a-8617-27f0360650f3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 661013b1fd709eb316b961b1db5fc30b3f4c8e66
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31468555"
---
# <a name="idiaenuminjectedsourcesclone"></a>IDiaEnumInjectedSources::Clone
現在の列挙子と同じ列挙の状態を含む列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT Clone (   
   IDiaEnumInjectedSources** ppenum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppenum`  
 [out]返します、 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)列挙子の重複を含むオブジェクトです。 挿入されたソースが重複していない、列挙子。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)