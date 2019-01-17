---
title: IScriptEntry::GetName |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetName
ms.assetid: 56daa288-618f-497c-a360-7d443afd478b
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c388340c35afe2ae7e5e7d0f5078e70b46c0b1bc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090884"
---
# <a name="iscriptentrygetname"></a>IScriptEntry::GetName
(関数) などの 1 つのオブジェクトを表すエントリの場合は、オブジェクトの名前を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbstr`  
 [out]によって表されるオブジェクトの名前、`IScriptEntry`スクリプト ブロック。 エントリが 1 つのオブジェクトを表していない場合は、NULL が返されます。  
  
 子のエントリは、1 つの関数オブジェクトを表します。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptNode:。:Createchildentry](../../winscript/reference/iscriptnode-createchildentry.md)