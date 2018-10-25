---
title: IDiaStackWalkHelper::put_registerValue |Microsoft Docs
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
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4256e281bb2b0a83660f1bb0aac11543d25a3eb9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49865428"
---
# <a name="idiastackwalkhelperputregistervalue"></a>IDiaStackWalkHelper::put_registerValue
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
  
## <a name="remarks"></a>Remarks  
 値のサイズに関係なく、実装はのみ何レジスタは、通常は保持を格納する必要があります。 たとえば、のみ、最下位 8 ビット指定された値の 8 ビット レジスタを保持します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV_HREG_e 列挙型](../../debugger/debug-interface-access/cv-hreg-e.md)



