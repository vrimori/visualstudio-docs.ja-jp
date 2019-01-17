---
title: Idiasymbol::get_platform |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_platform method
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e36f51dd977971c78c3ca7593c98dc00831ef2aa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53875139"
---
# <a name="idiasymbolgetplatform"></a>IDiaSymbol::get_platform
コンパイル単位のコンパイル対象のプラットフォームの種類を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_platform (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out]値を返します、 [CV_CPU_TYPE_e 列挙型](../../debugger/debug-interface-access/cv-cpu-type-e.md)コンパイル単位がコンパイルされたのプラットフォームを指定する列挙値を入力します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
> [!NOTE]
>  戻り値`S_FALSE`プロパティがシンボルを使用できないことを意味します。  
  
## <a name="see-also"></a>「  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV_CPU_TYPE_e 列挙型](../../debugger/debug-interface-access/cv-cpu-type-e.md)