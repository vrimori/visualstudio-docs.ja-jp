---
title: IDebugApplication::Close |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.Close
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::Close
ms.assetid: d19baa07-3f3b-47de-8185-5eb3e7ac8b46
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a861e2cbdfedc80747e9390316c47da43b71656
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087413"
---
# <a name="idebugapplicationclose"></a>IDebugApplication::Close
によりこのアプリケーションはすべての参照を解放し、非アクティブな状態を入力します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT Close();  
```  
  
#### <a name="parameters"></a>パラメーター  
 このメソッドには、パラメーターはありません。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 通常、アプリケーションの所有者は、アプリケーションの終了時にこのメソッドを呼び出します。  
  
 このメソッドにより`IApplicationDebugger::onClose`呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplication インターフェイス](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onClose](../../winscript/reference/iapplicationdebugger-onclose.md)