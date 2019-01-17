---
title: IScriptEntry::SetItemName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetItemName
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20af0975a4175d10b110ac5e3cef9e0055f4ce1b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097761"
---
# <a name="iscriptentrysetitemname"></a>IScriptEntry::SetItemName
識別する項目の名前を設定、`IScriptEntry`オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `psz`  
 [in]項目の名前を格納するバッファーのアドレス。 項目の名前は、エントリを識別するために、ホストによって使用されます。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_FAIL`|メソッドは成功しませんでした。|  
  
## <a name="remarks"></a>Remarks  
 `IScriptEntry`オブジェクトの場合、このメソッドが戻る`S_OK`します。  
  
 `IScriptScriptlet`オブジェクト (から派生する`IScriptEntry`)、このメソッドが戻る`E_FAIL`します。 `IScriptScriptlet`オブジェクトによって、項目の名前が設定されます[IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md)変更ことはできません。  
  
## <a name="see-also"></a>関連項目  
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)