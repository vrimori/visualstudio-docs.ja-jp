---
title: IDispatchEx::GetDispID |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c466ec767be53d100b970314bf0d81d5dd9dfb20
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097540"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
1 つのメンバー名を対応するように DISPID を後続の呼び出しのために使用する、マップ`IDispatchEx::InvokeEx`します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bstrName`  
 マップする名前で渡されます。  
  
 `grfdex`  
 メンバー識別子を取得するためのオプションを決定します。 次の値の組み合わせを指定できます。  
  
|[値]|説明|  
|-----------|-------------|  
|fdexNameCaseSensitive|名前参照は、大文字と小文字で実行するように要求します。 大文字のルックアップをサポートしていないオブジェクトによって無視可能性があります。|  
|fdexNameEnsure|存在しない場合、メンバーを作成することを要求します。 値で、新しいメンバーを作成する必要があります`VT_EMPTY`します。|  
|fdexNameImplicit|ベース オブジェクトが明示的に指定されていない場合に、呼び出し元が特定の名前のメンバーのオブジェクトを検索することを示します。|  
|fdexNameCaseInsensitive|名前参照で大文字と小文字を行うように要求します。 大文字のルックアップをサポートしていないオブジェクトによって無視可能性があります。|  
  
 `pid`  
 DISPID 結果を受信する呼び出し元が割り当てた場所へのポインター。 エラーが発生する場合`pid`DISPID_UNKNOWN が含まれています。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|メモリ不足です。|  
|`DISP_E_UNKNOWNNAME`|名前が不明です。|  
  
## <a name="remarks"></a>Remarks  
 `GetDispID` 代わりに使用できる`GetIDsOfNames`指定されたメンバーの DISPID を取得します。  
  
 `IDispatchEx`追加と削除、メンバーの Dispid のセットの一定していないオブジェクトの有効期間を使用します。  
  
 未使用`riid`パラメーター`IDispatch::GetIDsOfNames`が削除されました。  
  
## <a name="example"></a>例  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>関連項目  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)