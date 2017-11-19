---
title: "IDispatchEx::GetDispID |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93595cd2d0f88244866ab7363ecd68c6d8073b48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
1 つのメンバー名に対応する DISPID、後続の呼び出しのために使用するマップ`IDispatchEx::InvokeEx`です。  
  
## <a name="syntax"></a>構文  
  
```  
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
 メンバー識別子を取得するためのオプションが決まります。 これにより、次の値の組み合わせが可能します。  
  
|値|説明|  
|-----------|-------------|  
|fdexNameCaseSensitive|大文字と小文字で名前の参照は実行を要求します。 大文字小文字を区別する検索をサポートしていないオブジェクトでは無視できます。|  
|fdexNameEnsure|既に存在しない場合、メンバーを作成することを要求します。 新しいメンバーを値で作成する必要があります`VT_EMPTY`です。|  
|fdexNameImplicit|ベース オブジェクトが明示的に指定されていない場合に、呼び出し元が特定の名前のメンバーのオブジェクトを検索することを示します。|  
|fdexNameCaseInsensitive|大文字と小文字で名前の参照は実行を要求します。 大文字と小文字の参照をサポートしていないオブジェクトでは無視できます。|  
  
 `pid`  
 DISPID 結果を受信する呼び出し元が割り当てた場所へのポインター。 エラーが発生する場合`pid`DISPID_UNKNOWN が含まれています。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|メモリ不足です。|  
|`DISP_E_UNKNOWNNAME`|名前が不明です。|  
  
## <a name="remarks"></a>コメント  
 `GetDispID`代わりに使用できる`GetIDsOfNames`を特定のメンバーの DISPID を取得します。  
  
 `IDispatchEx`追加と削除、メンバーの Dispid のセットの一定していないオブジェクトの有効期間を使用します。  
  
 未使用`riid`パラメーター`IDispatch::GetIDsOfNames`は削除されました。  
  
## <a name="example"></a>例  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>関連項目  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)