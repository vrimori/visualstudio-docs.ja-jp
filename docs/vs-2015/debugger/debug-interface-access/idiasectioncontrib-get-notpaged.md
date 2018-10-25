---
title: Idiasectioncontrib::get_notpaged |Microsoft Docs
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
- IDiaSectionContrib::get_notPaged method
ms.assetid: bb6baa40-fece-4a4c-aba9-f4b41f418f8b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a30df12e8058943a37bd4afd5e986b597a918ea9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49849919"
---
# <a name="idiasectioncontribgetnotpaged"></a>IDiaSectionContrib::get_notPaged
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

メモリ不足のセクションがページングされることはできないかどうかを示すフラグを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT get_notPaged (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out, retval]返します`TRUE`場合は、セクションは、それ以外の場合以外にページングされることはできません、返します`FALSE`します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`します。 返します`S_FALSE`場合、このプロパティはサポートされていません。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



