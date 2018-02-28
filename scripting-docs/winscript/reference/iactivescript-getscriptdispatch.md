---
title: "IActiveScript::GetScriptDispatch |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b2f09934cf6d2bb28f7dae93d0bf49c8dc7437d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
取得、`IDispatch`メソッドおよびプロパティが現在実行中のスクリプトに関連付けられているためのインターフェイスです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrItemName`  
 [in]呼び出し元が関連付けられているディスパッチ オブジェクト必要がある項目の名前を格納するバッファーのアドレスです。 このパラメーターが場合`NULL`、ディスパッチ オブジェクトがスクリプトによって定義されたすべてのグローバル メソッドとプロパティのメンバーとして含まれています。 を介して、`IDispatch`インターフェイスと関連付けられている`ITypeInfo`インターフェイス、ホストは、スクリプト メソッドまたはビューを起動およびスクリプト変数を変更できます。  
  
 `ppdisp`  
 [out]スクリプトのグローバル メソッドとプロパティに関連付けられているオブジェクトへのポインターを受け取る変数のアドレスです。 スクリプト エンジンが、このようなオブジェクトをサポートしていない場合`NULL`が返されます。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれたまたは初期化) します。|  
|`S_FALSE`|スクリプト エンジンがディスパッチ オブジェクト; をサポートしていません`ppdisp`パラメーターが NULL に設定します。|  
  
## <a name="remarks"></a>コメント  
 メソッドとプロパティを呼び出すことによって追加できるため、 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) 、インターフェイス、`IDispatch`このメソッドによって返されるインターフェイスは、動的に新しいメソッドとプロパティをサポートできます。 同様に、`IDispatch::GetTypeInfo`メソッドが返す、新しい一意`ITypeInfo`インターフェイスのメソッドとプロパティが追加されるとします。 ただし、言語エンジンが変更する必要があります、 `IDispatch` 、方法と互換性のないいずれかのインターフェイス以前`ITypeInfo`インターフェイスが返されます。 意味するなどを Dispid は決して再利用されます。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)