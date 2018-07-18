---
title: IPerPropertyBrowsing2::GetPredefinedStrings |Microsoft ドキュメント
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
ms.openlocfilehash: e07d52eca9434acc7e54f3b35b111cf12af0a871
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729252"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
このプロパティの潜在的な値を表す文字列のポインターのカウント対象の配列とリスト ボックスに入力する、呼び出し元を使用できます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dispid`  
 [in]呼び出し元は、対象の文字列のリストを要求しているプロパティの識別子をディスパッチします。  
  
 `pCaStrings`  
 [out]要素の数と、メソッドに割り当てられたポインターの配列の文字列のアドレスを含む呼び出し元が割り当てた、カウント対象の配列構造体へのポインター。 メソッドが失敗した場合、メモリを割り当てられません、構造体の内容は未定義です。  
  
 `pCaCookies`  
 [out]要素の数と Dword のメソッドに割り当てられた配列のアドレスを含む呼び出し元が割り当てた、カウント対象の配列構造へのポインター。 メソッドが失敗した場合、メモリを割り当てられません、構造体の内容は未定義です。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`通常`S_OK`です。  
  
## <a name="see-also"></a>関連項目  
 [IPerPropertyBrowsing2 インターフェイス 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)