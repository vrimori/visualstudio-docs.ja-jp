---
title: IDiaSession::findSymbolsForAcceleratorPointerTag |Microsoft Docs
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
ms.assetid: 95fd5e7a-c637-437e-b369-c864eef733c2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af1a90ea4fd35ec73ecc043301a535214e294c7a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49813883"
---
# <a name="idiasessionfindsymbolsforacceleratorpointertag"></a>IDiaSession::findSymbolsForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

親のアクセラレータのスタブ関数で指定したタグ値に対応する変数のシンボルの列挙を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
HRESULT findSymbolsForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `parent`  
 [in]検索するアクセラレータのスタブ関数に対応する IDiaSymbol します。  
  
 `tagValue`  
 [in]ポインターのタグ値。  
  
 `ppResult`  
 [out]ポインター、`IDiaEnumSymbols`インターフェイス ポインターでは、結果を使用して初期化します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)



