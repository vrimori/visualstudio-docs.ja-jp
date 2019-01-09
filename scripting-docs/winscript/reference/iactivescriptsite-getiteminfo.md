---
title: Iactivescriptsite::getiteminfo |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetItemInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetItemInfo
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f4dc6515d64406870ca10f003d7cea515c49b7d8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095889"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
により、スクリプト エンジンを使用して追加の項目に関する情報を取得する、 [iactivescript::addnameditem](../../winscript/reference/iactivescript-addnameditem.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrName`  
 [in]指定されている、項目に関連付けられた名前、 [iactivescript::addnameditem](../../winscript/reference/iactivescript-addnameditem.md)メソッド。  
  
 `dwReturnMask`  
 [in]項目に関する情報を返す必要がありますを指定するビット マスクです。 スクリプト エンジンは最小限の情報を要求する必要があります、戻り値パラメーターの一部 (たとえば、 `ITypeInfo`) の読み込みまたは生成に時間がかかることができます。 次の値の組み合わせになります。  
  
|[値]|説明|  
|-----------|-------------|  
|される SCRIPTINFO_IUNKNOWN|返します、`IUnknown`この項目のインターフェイス。|  
|SCRIPTINFO_ITYPEINFO|返します、`ITypeInfo`この項目のインターフェイス。|  
  
 `ppunkItem`  
 [out]ポインターを受け取る変数のアドレス、`IUnknown`特定の項目に関連付けられているインターフェイス。 スクリプト エンジンを使用できる、`IUnknown::QueryInterface`メソッドを取得する、`IDispatch`の項目のインターフェイス。 場合、このパラメーターは NULL を受け取ります`dwReturnMask`される SCRIPTINFO_IUNKNOWN 値は含まれません。 NULL を受信、項目の名前に関連付けられているオブジェクトが存在しない場合も、このメカニズムは SCRIPTITEM_CODEONLY フラグ設定で名前付きの項目が追加されたときに、単純なクラスを作成するために使用、 [iactivescript::addnameditem](../../winscript/reference/iactivescript-addnameditem.md)メソッド。  
  
 `ppTypeInfo`  
 [out]ポインターを受け取る変数のアドレス、`ITypeInfo`アイテムに関連付けられているインターフェイス。 場合、このパラメーターは NULL を受け取ります`dwReturnMask`SCRIPTINFO_ITYPEINFO の値を含まない型情報がこの項目を使用できない場合またはします。 型情報が利用できない場合は、オブジェクトは、イベント ソースことはできません名のバインドを実現する必要があります、`IDispatch::GetIDsOfNames`メソッド。 なお、`ITypeInfo`オブジェクトは、複数のインターフェイスとイベント インターフェイスをサポート可能性がありますので、インターフェイスの取得は、項目のコクラス (TKIND_COCLASS) について説明します。 項目がサポートしている場合、`IProvideMultipleTypeInfo`インターフェイス、`ITypeInfo`取得インターフェイスは、インデックス 0 の場合と同じ`ITypeInfo`を使用して取得すると、`IProvideMultipleTypeInfo::GetInfoOfIndex`メソッド。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`TYPE_E_ELEMENTNOTFOUND`|指定した名前の項目は見つかりませんでした。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドによって示される情報のみを取得、`dwReturnMask`パラメーターの場合パフォーマンスが向上します。 たとえば場合、`ITypeInfo`インターフェイス項目は必要ありません、単に指定されていないで`dwReturnMask`します。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)