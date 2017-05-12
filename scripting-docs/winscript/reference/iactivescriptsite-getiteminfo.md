---
title: "IActiveScriptSite::GetItemInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetItemInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetItemInfo"
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetItemInfo
スクリプト エンジンが [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) のメソッドで追加された項目に関する情報を取得できます。  
  
## 構文  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### パラメーター  
 `pstrName`  
 \[入力\] [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) のメソッドで指定された項目に関連付けられた名前。  
  
 `dwReturnMask`  
 \[入力\]ビットマスクの項目に関してどの情報を返す必要があるかを指定します。  スクリプト エンジンは戻り値パラメーターの一部は \(たとえば、\) `ITypeInfo`読み込むか、または生成にかなりの時間がかかるため、可能な最小限の情報を要求する必要があります。  次の値の組み合わせがあります:  
  
|値|説明|  
|-------|--------|  
|SCRIPTINFO\_IUNKNOWN|この項目の `IUnknown` のインターフェイスを返します。|  
|SCRIPTINFO\_ITYPEINFO|この項目の `ITypeInfo` のインターフェイスを返します。|  
  
 `ppunkItem`  
 \[入力\] `IUnknown` のインターフェイスへのポインターを受け取る変数のアドレスは、特定の項目に関連付けられた  スクリプト エンジンは、アイテムの `IDispatch` のインターフェイスを取得するに `IUnknown::QueryInterface` のメソッドを使用できます。  このパラメーターは `dwReturnMask` が SCRIPTINFO\_IUNKNOWN の値が null 値を受け取ります。  または、項目の名前が付けられたオブジェクトが存在しない場合、null 値を受け取ります。; 名前付きの項目が [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) のメソッドで設定された SCRIPTITEM\_CODEONLY フラグによって追加されたときに、この機構は単純なクラスを作成するために使用されます。  
  
 `ppTypeInfo`  
 \[入力\] `ITypeInfo` のインターフェイスへのポインターを受け取る変数のアドレスは、項目に関連付けられた  このパラメーターは `dwReturnMask` が SCRIPTINFO\_ITYPEINFO の値が含まれていない場合、または型情報がこの項目の利用できない場合は NULL を受け取ります。  型情報が存在しない場合、は、ソース イベントできず、名前のバインディングが `IDispatch::GetIDsOfNames` のメソッドで実現する必要があります。  オブジェクトが複数のインターフェイスとイベント インターフェイスをサポートする可能性があるから取得される `ITypeInfo` のインターフェイスは項目のコクラス \(TKIND\_COCLASS\) を記述することに注意してください。  項目が `IProvideMultipleTypeInfo` のインターフェイスをサポートしている場合、取得した `ITypeInfo` のインターフェイスは `IProvideMultipleTypeInfo::GetInfoOfIndex` のメソッドを使用して取得したインデックス `ITypeInfo` 同じです。  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`TYPE_E_ELEMENTNOTFOUND`|指定した名前の項目が見つかりませんでした。|  
  
## 解説  
 このメソッドは `dwReturnMask` のパラメーターに表示する情報のみを取得します; これによって、パフォーマンスが向上します。  たとえば、`ITypeInfo` のインターフェイスが項目のために必要でない場合、`dwReturnMask`で単に指定されません。  
  
## 参照  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)