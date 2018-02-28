---
title: "IDispatchEx::GetMemberProperties |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d216bb7b21c8895337b9925007637c00d0deb37
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
メンバーのプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `id`  
 メンバーを識別します。 使用して`GetDispID`または`GetNextDispID`ディスパッチ識別子を取得します。  
  
 `grfdexFetch`  
 取得するプロパティを決定します。 値の組み合わせが可能ですこの`pgrfdex`や、次の値の組み合わせ。  
  
|値|説明|  
|-----------|-------------|  
|grfdexPropCanAll|FdexPropCanGet、fdexPropCanPut、fdexPropCanPutRef、fdexPropCanCall、fdexPropCanConstruct および fdexPropCanSourceEvents を結合します。|  
|grfdexPropCannotAll|FdexPropCannotGet、fdexPropCannotPut、fdexPropCannotPutRef、fdexPropCannotCall、fdexPropCannotConstruct および fdexPropCannotSourceEvents を結合します。|  
|grfdexPropExtraAll|FdexPropNoSideEffects と fdexPropDynamicType を結合します。|  
|grfdexPropAll|GrfdexPropCanAll、grfdexPropCannotAll および grfdexPropExtraAll を結合します。|  
  
 `pgrfdex`  
 アドレス、`DWORD`要求されたプロパティを受け取る。 これにより、次の値の組み合わせが可能します。  
  
|値|説明|  
|-----------|-------------|  
|fdexPropCanGet|メンバーは、DISPATCH_PROPERTYGET を使用して取得できます。|  
|fdexPropCannotGet|DISPATCH_PROPERTYGET を使用して、メンバーを取得できません。|  
|fdexPropCanPut|メンバーは、DISPATCH_PROPERTYPUT を使用して設定できます。|  
|fdexPropCannotPut|DISPATCH_PROPERTYPUT を使用してメンバーを設定することはできません。|  
|fdexPropCanPutRef|メンバーは、DISPATCH_PROPERTYPUTREF を使用して設定できます。|  
|fdexPropCannotPutRef|DISPATCH_PROPERTYPUTREF を使用してメンバーを設定することはできません。|  
|fdexPropNoSideEffects|メンバーには、すべての副作用はありません。 たとえば、デバッガーが安全に取得/設定/の呼び出しをでした、スクリプトのデバッグ中の状態を変更せずには、このメンバー。|  
|fdexPropDynamicType|メンバーは、動的オブジェクトの有効期間中に変更できます。|  
|fdexPropCanCall|メンバーは、DISPATCH_METHOD を使用して、メソッドとして呼び出すことができます。|  
|fdexPropCannotCall|メンバーは、DISPATCH_METHOD を使用して、メソッドとして呼び出すことはできません。|  
|fdexPropCanConstruct|メンバーは、DISPATCH_CONSTRUCT を使用してコンス トラクターとして呼び出すことができます。|  
|fdexPropCannotConstruct|メンバーは、DISPATCH_CONSTRUCT を使用してコンス トラクターとして呼び出すことはできません。|  
|fdexPropCanSourceEvents|メンバーは、イベントを発生させることができます。|  
|fdexPropCannotSourceEvents|メンバーは、イベントを発生させることはできません。|  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`DISP_E_UNKNOWNNAME`|名前が不明です。|  
  
## <a name="example"></a>例  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>関連項目  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)