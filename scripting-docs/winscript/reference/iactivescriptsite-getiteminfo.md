---
title: IActiveScriptSite::GetItemInfo |Microsoft ドキュメント
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
ms.openlocfilehash: ccb898c14571d1f1fd1fcae7cb0b9a6d322f2754
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24725422"
---
# <a name="iactivescriptsitegetiteminfo"></a>IActiveScriptSite::GetItemInfo
により、スクリプト エンジンを使用して追加の項目に関する情報を取得する、 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrName`  
 [in]指定されている、項目に関連付けられている名前、 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)メソッドです。  
  
 `dwReturnMask`  
 [in]どのような項目に関する情報が返される必要がありますを指定するビット マスクです。 スクリプト エンジンは最小限の考えられる情報を要求する必要があります戻り値パラメーターの一部 (たとえば、 `ITypeInfo`) の読み込みまたは生成に時間がかかることができます。 次の値の組み合わせが可能です。  
  
|値|説明|  
|-----------|-------------|  
|SCRIPTINFO_IUNKNOWN|返します、`IUnknown`この項目のインターフェイスです。|  
|SCRIPTINFO_ITYPEINFO|返します、`ITypeInfo`この項目のインターフェイスです。|  
  
 `ppunkItem`  
 [out]ポインターを受け取る変数のアドレス、`IUnknown`指定したアイテムに関連付けられているインターフェイス。 スクリプト エンジンが使用できる、`IUnknown::QueryInterface`を取得するメソッド、`IDispatch`アイテムに対するインターフェイスです。 場合、このパラメーターは NULL を受け取ります`dwReturnMask`SCRIPTINFO_IUNKNOWN 値は含まれません。 また、受信 NULL、項目の名前に関連付けられたオブジェクトが存在しない場合このメカニズムは SCRIPTITEM_CODEONLY は、フラグ設定で、名前付きの項目が追加されたときに、単純なクラスを作成するために使用、 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)メソッドです。  
  
 `ppTypeInfo`  
 [out]ポインターを受け取る変数のアドレス、`ITypeInfo`アイテムに関連付けられているインターフェイス。 場合、このパラメーターは NULL を受け取ります`dwReturnMask`SCRIPTINFO_ITYPEINFO 値を含まない型情報がこの項目を使用できない場合またはします。 型情報が利用できない場合は、オブジェクトは、イベントをソースことはできません名のバインドを実現する必要があります、`IDispatch::GetIDsOfNames`メソッドです。 なお、`ITypeInfo`オブジェクトでサポートされる複数のインターフェイスとイベント インターフェイスを取得するインターフェイスに、項目のコクラス (TKIND_COCLASS) について説明します。 アイテムをサポートしている場合、 `IProvideMultipleTypeInfo` 、インターフェイス、`ITypeInfo`取得インターフェイスは、インデックス 0 と同じ`ITypeInfo`を取得するを使用して、`IProvideMultipleTypeInfo::GetInfoOfIndex`メソッドです。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`TYPE_E_ELEMENTNOTFOUND`|指定した名前の項目は見つかりませんでした。|  
  
## <a name="remarks"></a>コメント  
 このメソッドによって示される情報のみを取得、`dwReturnMask`パラメーターです。 これによりパフォーマンスが向上します。 たとえば場合、`ITypeInfo`インターフェイスは、アイテムには必要ありません、単に指定されていないで`dwReturnMask`です。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)