---
title: IDebugHelper::CreatePropertyBrowser |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3eedf9d6ed07b510d7912a5b28d23e0a1f05dda
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087751"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
バリアント型をラップするプロパティ ブラウザーを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pvar`  
 [in]参照するルートのバリアント。  
  
 `bstrName`  
 [in]ルートに付ける名前。  
  
 `pdat`  
 [in]プロパティを要求するスレッドします。 このパラメーターが NULL の場合は、マーシャ リングは実行されません。  
  
 `ppdob`  
 [out]プロパティ ブラウザー。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、バリアント型をラップするプロパティ ブラウザーを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper インターフェイス](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)