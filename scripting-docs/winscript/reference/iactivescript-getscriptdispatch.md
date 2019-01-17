---
title: Iactivescript::getscriptdispatch |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a18d6781ca2b7820686b317ad0be5da425ade1f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097683"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
取得、`IDispatch`メソッドと、現在実行中のスクリプトに関連付けられているプロパティのインターフェイス。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrItemName`  
 [in]呼び出し元が関連付けられているディスパッチ オブジェクト必要がある項目の名前を格納するバッファーのアドレス。 このパラメーターが場合`NULL`、ディスパッチ オブジェクトがスクリプトによって定義されたすべてのグローバル メソッドとプロパティのメンバーとして含まれています。 を通じて、`IDispatch`インターフェイスと関連付けられている`ITypeInfo`インターフェイス、ホストはスクリプト メソッドまたはビューを呼び出すし、スクリプト変数を変更します。  
  
 `ppdisp`  
 [out]スクリプトのグローバル メソッドとプロパティに関連付けられているオブジェクトへのポインターを受け取る変数のアドレス。 スクリプト エンジンは、このようなオブジェクトをサポートしていない場合`NULL`が返されます。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれるまたは初期化) します。|  
|`S_FALSE`|スクリプト エンジンがディスパッチ オブジェクト; をサポートしていません`ppdisp`パラメーターが NULL に設定されます。|  
  
## <a name="remarks"></a>Remarks  
 メソッドとプロパティを呼び出すことによって追加できるため、 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) 、インターフェイス、`IDispatch`このメソッドによって返されるインターフェイスには、新しいメソッドとプロパティに動的をサポートできます。 同様に、`IDispatch::GetTypeInfo`メソッドが返す、新しい一意`ITypeInfo`インターフェイスのメソッドとプロパティが追加されたときにします。 ただし、言語エンジンは変更できないこと、`IDispatch`インターフェイスのいずれかと互換性が以前`ITypeInfo`インターフェイスが返されます。 つまり、たとえば、Dispid が決して再利用があります。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)