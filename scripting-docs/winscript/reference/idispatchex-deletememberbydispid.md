---
title: IDispatchEx::DeleteMemberByDispID |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByDispID method
ms.assetid: f61231e5-ba93-4ac3-bde8-d363548356b3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de99e74cf12939a31c99cdc59ce8ad7fd685ae03
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086867"
---
# <a name="idispatchexdeletememberbydispid"></a>IDispatchEx::DeleteMemberByDispID
メンバーの DISPID を削除します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT DeleteMemberByDispID(  
    DISPID id  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `id`  
 メンバーの識別子です。 使用して`GetDispID`または`GetNextDispID`ディスパッチ識別子を取得します。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|メンバーが存在しますが、削除できません。|  
  
## <a name="remarks"></a>Remarks  
 DISPID が有効でする必要がある場合は、メンバーを削除すると、`GetNextDispID`します。  
  
 指定された名前を持つメンバーが削除され、後で同じ名前のメンバーが再作成された場合、DISPID は同じである必要があります。 (大文字と小文字が異なるだけのメンバー名が「同一」かどうかはオブジェクトに依存) です。  
  
## <a name="example"></a>例  
  
```cpp
BSTR bstrName;  
DISPID dispid;  
IDispatchEx *pdex;   
  
// Assign to pdex and bstrName  
if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
    pdex->DeleteMemberByDispID(dispid);  
```  
  
## <a name="see-also"></a>関連項目  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)