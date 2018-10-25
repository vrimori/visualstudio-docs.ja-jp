---
title: IDiaSymbol::get_numberOfAcceleratorPointerTags |Microsoft Docs
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
ms.assetid: 1886e3ec-b227-4187-8d93-c5144b4b77ae
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 480e6b7dda7c8790cd81a84ab9a8f860a894ca2d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208872"
---
# <a name="idiasymbolgetnumberofacceleratorpointertags"></a>IDiaSymbol::get_numberOfAcceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

C++ AMP のスタブ関数では、アクセラレータのポインターのタグの数を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT get_numberOfAcceleratorPointerTags(   
   DWORD* count);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `count`  
 [out]ポインターを`DWORD`で C++ AMP のスタブ関数ポインターのタグのアクセラレータの数を保持します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが、 `IDiaSymbol` C++ AMP のアクセラレータのスタブ関数に対応するインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



