---
title: "IDispatchEx::DeleteMemberByName |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cb9a9dfd979954c42101fde41819d7e12db59e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
名前でメンバーを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bstrName`  
 削除するメンバーの名前です。  
  
 `grfdex`  
 かどうか、メンバー名は大文字と小文字を決定します。 次の値のいずれかになります。  
  
|値|説明|  
|-----------|-------------|  
|fdexNameCaseSensitive|大文字と小文字で名前の参照は実行を要求します。 大文字小文字を区別する検索をサポートしていないオブジェクトでは無視できます。|  
|fdexNameCaseInsensitive|大文字と小文字で名前の参照は実行を要求します。 大文字と小文字の参照をサポートしていないオブジェクトでは無視できます。|  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`S_FALSE`|メンバーが存在しますが、削除できません。|  
  
## <a name="remarks"></a>コメント  
 DISPID が有効のままに必要な場合は、メンバーを削除すると、`GetNextDispID`です。  
  
 名前が指定されたメンバーを削除し、後で同じ名前のメンバーが再作成されると、DISPID を同じにする必要があります。 (大文字小文字のみが異なるメンバーが「同一」かどうか、オブジェクトに依存する) です。  
  
## <a name="example"></a>例  
  
```  
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>関連項目  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)