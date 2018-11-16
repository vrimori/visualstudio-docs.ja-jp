---
title: IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag |Microsoft Docs
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
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 80edb1ce6f893bbab4d41e489f00dbc62337b424
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791359"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

対応するタグの値を指定すると、このメソッドは、指定の相対仮想アドレスにある場合は、このスタブ関数に含まれているシンボルの列挙体を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `tagValue`  
 [in]Pointee シンボル レコードを検出するポインターのタグ値。  
  
 `rva`  
 [in]指定したタグ値を持つ pointee 変数に対応するシンボルをフィルター処理に使用される rva を示します。  
  
 `ppResult`  
 [out]ポインター、`IDiaEnumSymbols`結果で初期化されるインターフェイス ポインター。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`またはエラー コード。  
  
## <a name="remarks"></a>Remarks  
 のみこのメソッドを呼び出し、`IDiaSymbol`アクセラレータのスタブ関数に対応するインターフェイス。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)



