---
title: Idiaimagedata::get_imagebase |Microsoft Docs
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
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 278ea226c9531cdf16cc7660bb4eba67860430a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547805"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[idiaimagedata::get_imagebase](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaimagedata-get-imagebase)します。  
  
イメージのベースでのメモリ位置を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]推奨されるイメージのベース値を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 イメージ ベースの競合によってイメージは、可能性がありますにリベースされます自動的には、未使用のメモリの場所が読み込まれるときにします。 このメソッドは、コンパイル時に、モジュールに格納された基本ヒント (推奨されるメモリの場所) を返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)



