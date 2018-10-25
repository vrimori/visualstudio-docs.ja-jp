---
title: Idiastackwalkframe::put_registervalue |Microsoft Docs
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
- IDiaStackWalkFrame::put_registerValue method
ms.assetid: 2d8b79b6-7240-43fe-b24e-e4ff3e2c15b0
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ac8f1b438b1e2b0136df393d73cc614c9eecca
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828870"
---
# <a name="idiastackwalkframeputregistervalue"></a>IDiaStackWalkFrame::put_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

レジスタの値を設定します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `index`  
 [in]値、 [CV_HREG_e 列挙型](../../debugger/debug-interface-access/cv-hreg-e.md)への書き込みにレジスタを指定する列挙体。  
  
 `NewVal`  
 [in]新しい値を登録します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [CV_HREG_e 列挙型](../../debugger/debug-interface-access/cv-hreg-e.md)



