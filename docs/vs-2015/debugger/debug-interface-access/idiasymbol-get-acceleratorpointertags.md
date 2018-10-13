---
title: IDiaSymbol::get_acceleratorPointerTags |Microsoft Docs
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
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 28b38d7e87862822d9bf8f1e5c729629486f44d5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236094"
---
# <a name="idiasymbolgetacceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

C++ AMP のアクセラレータのスタブ関数に対応するすべてのアクセラレータ ポインター タグ値を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cnt`  
 [in]出力配列のサイズ`pPointerTags`します。  
  
 `pcnt`  
 [out]C++ AMP のアクセラレータのスタブ関数でアクセラレータ ポインター タグの数。  
  
 `pPointerTags`  
 [out]A `DWORD` C++ AMP のアクセラレータのスタブ関数でアクセラレータ ポインター タグの値が入力配列のポインター。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="remarks"></a>Remarks  
 このメソッドが、 `IDiaSymbol` C++ AMP のアクセラレータのスタブ関数に対応するインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



