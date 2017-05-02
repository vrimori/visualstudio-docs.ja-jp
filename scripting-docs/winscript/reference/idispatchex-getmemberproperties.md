---
title: "IDispatchEx::GetMemberProperties | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetMemberProperties
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetMemberProperties メソッド"
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetMemberProperties
メンバーのプロパティを取得します。  
  
## 構文  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### パラメーター  
 `id`  
 メンバーを識別します。  ディスパッチ ID を取得または `GetNextDispID` 使用 `GetDispID`。  
  
 `grfdexFetch`  
 取得するプロパティを決定します。  これは `pgrfdex` の下に表示されている値の組み合わせや次の値の組み合わせです:  
  
|値|説明|  
|-------|--------|  
|grfdexPropCanAll|fdexPropCanGet、fdexPropCanPut、fdexPropCanPutRef、fdexPropCanCall、fdexPropCanConstruct と fdexPropCanSourceEvents を結合します。|  
|grfdexPropCannotAll|fdexPropCannotGet、fdexPropCannotPut、fdexPropCannotPutRef、fdexPropCannotCall、fdexPropCannotConstruct と fdexPropCannotSourceEvents を結合します。|  
|grfdexPropExtraAll|結合の fdexPropNoSideEffects と fdexPropDynamicType。|  
|grfdexPropAll|grfdexPropCanAll、grfdexPropCannotAll と grfdexPropExtraAll を結合します。|  
  
 `pgrfdex`  
 要求されたプロパティを受け取る `DWORD` のアドレス。  これは、次の値の組み合わせです:  
  
|値|説明|  
|-------|--------|  
|fdexPropCanGet|メンバーは DISPATCH\_PROPERTYGET を使用して取得できます。|  
|fdexPropCannotGet|メンバーは DISPATCH\_PROPERTYGET を使用して取得できません。|  
|fdexPropCanPut|メンバーは DISPATCH\_PROPERTYPUT を使用して設定できます。|  
|fdexPropCannotPut|メンバーは DISPATCH\_PROPERTYPUT を使用して設定できません。|  
|fdexPropCanPutRef|メンバーは DISPATCH\_PROPERTYPUTREF を使用して設定できます。|  
|fdexPropCannotPutRef|メンバーは DISPATCH\_PROPERTYPUTREF を使用して設定できません。|  
|fdexPropNoSideEffects|メンバーは副作用はありません。  たとえば、デバッガーは\/セットと呼び出しこのメンバー デバッグ スクリプトの状態を変更せずに取得するに安全にできます。|  
|fdexPropDynamicType|メンバーは動的なので、オブジェクトの有効期間中に変更できます。|  
|fdexPropCanCall|メンバーは DISPATCH\_METHOD を使用してメソッドとして呼び出すことができます。|  
|fdexPropCannotCall|メンバーは DISPATCH\_METHOD を使用してメソッドとして呼び出すことはできません。|  
|fdexPropCanConstruct|メンバーは DISPATCH\_CONSTRUCT を使用するコンストラクターとして呼び出すことができます。|  
|fdexPropCannotConstruct|メンバーは DISPATCH\_CONSTRUCT を使用するコンストラクターとして呼び出すことはできません。|  
|fdexPropCanSourceEvents|メンバーはイベントを発生させるできます。|  
|fdexPropCannotSourceEvents|メンバーはイベントを発生させることができません。|  
  
## 戻り値  
 次の値の場合: 1  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`DISP_E_UNKNOWNNAME`|名前は不明ですいません。|  
  
## 使用例  
  
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
  
## 参照  
 [IDispatchEx インターフェイス](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)