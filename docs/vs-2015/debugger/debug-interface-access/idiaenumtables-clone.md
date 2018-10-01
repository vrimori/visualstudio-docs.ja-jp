---
title: Idiaenumtables::clone |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaEnumTables::Clone method
ms.assetid: beb21109-b12c-44d8-8c1f-a332216b3713
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfb80dcf97fd47404f262da46c7aad08b91f6830
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537171"
---
# <a name="idiaenumtablesclone"></a>IDiaEnumTables::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[idiaenumtables::clone](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaenumtables-clone)します。  
  
現在の列挙子と同じ列挙状態を格納する列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumTables** ppenum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppenum`  
 [out]返します、 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)列挙子の重複を含むオブジェクト。 テーブルが重複していない、列挙子。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)



