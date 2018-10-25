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
ms.openlocfilehash: a60225e69a04399a3ff0160291b84e9f3fda513c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49915965"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
このプロパティの潜在的な値を表す文字列のポインターの counted 配列とリスト ボックスに入力して、呼び出し元を使用できます。  
  
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
 [in]呼び出し元の文字列リストを要求しているプロパティのディスパッチ識別子。  
  
 `pCaStrings`  
 [out]要素の数と文字列のポインターのメソッドによって割り当てられた配列のアドレスを格納する配列を呼び出し元が割り当てた、カウントされた構造体へのポインター。 メソッドが失敗した場合、メモリが割り当てられていないと構造体の内容が定義されていません。  
  
 `pCaCookies`  
 [out]呼び出し元割り当てへのポインターには、要素の数と Dword メソッドによって割り当てられた配列のアドレスを含む配列構造がカウントされます。 メソッドが失敗した場合、メモリが割り当てられていないと構造体の内容が定義されていません。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`、通常`S_OK`します。  
  
## <a name="see-also"></a>関連項目  
 [IPerPropertyBrowsing2 インターフェイス 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)