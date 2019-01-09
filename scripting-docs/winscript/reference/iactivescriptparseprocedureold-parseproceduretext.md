---
title: IActiveScriptParseProcedureOld::ParseProcedureText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec100214a43be6e1faf5e229ce6452432065002b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093393"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
指定したコードのプロシージャを解析し、匿名のプロシージャを名前空間に追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrCode`  
 [in]評価するプロシージャのテキスト。 この文字列の解釈はスクリプト言語によって異なります。  
  
 `pstrFormalParams`  
 [in]プロシージャの仮パラメーター名。 パラメーター名は、スクリプト エンジンの適切な区切り記号で区切る必要があります。 名前をかっこで囲まれていない必要があります。  
  
 `pstrItemName`  
 [in]プロシージャが評価されるコンテキストを提供する名前付きの項目の名前。 このパラメーターは場合`NULL`コードは、スクリプト エンジンのグローバルなコンテキストで評価されます。  
  
 `punkContext`  
 [in]コンテキスト オブジェクト。 このオブジェクトはデバッグ環境用に予約されています。アクティブなランタイム コンテキストを表すためにデバッガーによって指定される場合があります。 このパラメーターは、する場合`NULL`、エンジンを使用して`pstrItemName`コンテキストを識別するためにします。  
  
 `pstrDelimiter`  
 [in]プロシージャの末尾の区切り記号。 ときに`pstrCode`解析は、テキストのストリームからホスト通常を使用して、区切り記号、2 つの単一引用符 (")、プロシージャの終了を検出するなど。 このパラメーターは、いくつかの条件を提供するスクリプト エンジンをできるように、ホストが使用される区切り記号を指定します (たとえば、単一引用符 (') を区切り記号として使用するための 2 つの単一引用符に置き換える) のプリミティブな前処理します。 正確に把握 (および場合は) この情報は、スクリプト エンジンによって異なります、スクリプト エンジンが使用されます。 このパラメーターに設定`NULL`ホストでは、プロシージャの終わりをマークする、区切り記号を使用しなかった場合。  
  
 `dwSourceContextCookie`  
 [in]デバッグのために使用するアプリケーション定義の値。  
  
 `ulStartingLineNumber`  
 [in]解析は、行の位置を指定するゼロベースの値が開始されます。  
  
 `dwFlags`  
 [in]プロシージャに関連付けられているフラグです。 これらの値の組み合わせを指定できます。  
  
|定数|[値]|説明|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|示しますコードでは、`pstrCode`プロシージャの戻り値を表す式を指定します。|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|示します、`this`ポインターは、プロシージャのスコープに含まれます。|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|示しますの親、`this`ポインターは、プロシージャのスコープ内にあります。|  
  
 `ppdisp`  
 [out]既定の方法がこのメソッドによって解析され、プロシージャはディスパッチ ラッパーを返します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_NOTIMPL`|このメソッドはサポートされていません。 スクリプト エンジンは、名前空間には手順の実行時の追加をサポートしていません。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンは未初期化または終了状態)。|  
|`OLESCRIPT_E_SYNTAX`|手順で指定されていない構文エラーが発生しました。|  
|`S_FALSE`|スクリプト エンジンがディスパッチ オブジェクト; をサポートしていません`ppdisp`にパラメーターが設定されている`NULL`します。|  
  
## <a name="remarks"></a>Remarks  
 この呼び出し中にスクリプト コードは評価されません。上のメソッドに、プロシージャがコンパイルされる代わりに、`ppdisp`を呼び出すことができる、スクリプトによって後でします。  
  
 このインターフェイスが好評だったの非推奨とされます、`IActiveScriptParseProcedure`インターフェイス。 `IActiveScriptParseProcedure::ParseProcedureText`メソッドは、このメソッドに似ていますが、プロシージャ名を指定することができます。 すべての状況で`IActiveScriptParseProcedure::ParseProcedureText`使用する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptParseProcedureOld インターフェイス](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)