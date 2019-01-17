---
title: IPerPropertyBrowsing2::GetPredefinedStrings |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3bec9643a89d40a7b1e37d019d4211bd7167ee65
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088609"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
このプロパティの潜在的な値を表す文字列のポインターの counted 配列とリスト ボックスに入力して、呼び出し元を使用できます。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dispid`  
 [in]呼び出し元の文字列リストを要求しているプロパティのディスパッチ識別子。  
  
 `pCaStrings`  
 [out]要素の数と文字列のポインターのメソッドによって割り当てられた配列のアドレスを格納する配列を呼び出し元が割り当てた、カウントされた構造体へのポインター。 メソッドが失敗した場合、メモリが割り当てられていないと構造体の内容が定義されていません。  
  
 `pCaCookies`  
 [out]呼び出し元割り当てへのポインターには、要素の数と Dword メソッドによって割り当てられた配列のアドレスを含む配列構造がカウントされます。 メソッドが失敗した場合、メモリが割り当てられていないと構造体の内容が定義されていません。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`、通常`S_OK`します。  
  
## <a name="see-also"></a>関連項目  
 [IPerPropertyBrowsing2 インターフェイス 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)