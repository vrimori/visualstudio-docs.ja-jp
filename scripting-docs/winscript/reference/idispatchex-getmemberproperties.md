---
title: IDispatchEx::GetMemberProperties |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51e01ef3fa6d5e0611875f6402b79e53f8c83cac
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088193"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
メンバーのプロパティを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
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
 取得するプロパティを決定します。 これは、下に一覧表示の値の組み合わせ`pgrfdex`や、次の値の組み合わせ。  
  
|[値]|説明|  
|-----------|-------------|  
|grfdexPropCanAll|FdexPropCanGet、fdexPropCanPut、fdexPropCanPutRef、fdexPropCanCall、fdexPropCanConstruct および fdexPropCanSourceEvents を結合します。|  
|grfdexPropCannotAll|FdexPropCannotGet、fdexPropCannotPut、fdexPropCannotPutRef、fdexPropCannotCall、fdexPropCannotConstruct および fdexPropCannotSourceEvents を結合します。|  
|grfdexPropExtraAll|FdexPropNoSideEffects と fdexPropDynamicType を結合します。|  
|grfdexPropAll|GrfdexPropCanAll、grfdexPropCannotAll および grfdexPropExtraAll を結合します。|  
  
 `pgrfdex`  
 アドレスを`DWORD`要求されたプロパティを受け取る。 次の値の組み合わせを指定できます。  
  
|[値]|説明|  
|-----------|-------------|  
|fdexPropCanGet|メンバーは、DISPATCH_PROPERTYGET を使用して取得できます。|  
|fdexPropCannotGet|メンバーは、DISPATCH_PROPERTYGET を使用して取得することはできません。|  
|fdexPropCanPut|メンバーは、DISPATCH_PROPERTYPUT を使用して設定できます。|  
|fdexPropCannotPut|DISPATCH_PROPERTYPUT を使用して、メンバーを設定することはできません。|  
|fdexPropCanPutRef|メンバーは、DISPATCH_PROPERTYPUTREF を使用して設定できます。|  
|fdexPropCannotPutRef|DISPATCH_PROPERTYPUTREF を使用して、メンバーを設定することはできません。|  
|fdexPropNoSideEffects|メンバーには、すべての副作用はありません。 たとえば、デバッガーが安全に取得/設定/の呼び出しをでした、スクリプトのデバッグ中の状態を変更することがなく、このメンバー。|  
|fdexPropDynamicType|メンバーは動的であり、オブジェクトの有効期間中に変更できます。|  
|fdexPropCanCall|メンバーは、DISPATCH_METHOD を使用して、メソッドとして呼び出すことができます。|  
|fdexPropCannotCall|メンバーは、DISPATCH_METHOD を使用して、メソッドとして呼び出すことができません。|  
|fdexPropCanConstruct|メンバーは、DISPATCH_CONSTRUCT を使用してコンス トラクターとして呼び出すことができます。|  
|fdexPropCannotConstruct|メンバーは、DISPATCH_CONSTRUCT を使用して、コンス トラクターとして呼び出すことができません。|  
|fdexPropCanSourceEvents|メンバーは、イベントを発生させることができます。|  
|fdexPropCannotSourceEvents|メンバーは、イベントを発生させることはできません。|  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`DISP_E_UNKNOWNNAME`|名前が不明です。|  
  
## <a name="example"></a>例  
  
```cpp
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