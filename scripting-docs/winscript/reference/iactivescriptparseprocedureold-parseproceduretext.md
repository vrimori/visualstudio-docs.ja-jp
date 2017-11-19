---
title: "IActiveScriptParseProcedureOld::ParseProcedureText |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptParseProcedureOld.ParseProcedureText
apilocation: jscript.dll
helpviewer_keywords: IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab546deb390535fa8ff71e116a0ad42d33cc104
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
指定したコードのプロシージャを解析し、匿名のプロシージャを名前空間に追加します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]プロシージャの仮パラメーター名。 パラメーター名は、スクリプト エンジンの適切な区切り記号で区切る必要があります。 名前は、かっこで囲まれていない必要があります。  
  
 `pstrItemName`  
 [in]プロシージャが評価されるコンテキストを示す名前付きの項目の名前。 このパラメーターが場合`NULL`コードは、スクリプト エンジンのグローバル コンテキストで評価されます。  
  
 `punkContext`  
 [in]コンテキスト オブジェクト。 このオブジェクトはデバッグ環境用に予約されています。アクティブなランタイム コンテキストを表すためにデバッガーによって指定される場合があります。 場合、このパラメーターは`NULL`、エンジンを使用して`pstrItemName`が、コンテキストを識別します。  
  
 `pstrDelimiter`  
 [in]最後の手順の区切り記号です。 ときに`pstrCode`解析は、テキストのストリームからホスト通常を使用して、区切り記号、2 つの単一引用符 (")、プロシージャの終了を検出するなどです。 このパラメーターがいくつかの条件を提供するスクリプト エンジンを許可する、ホストが使用する区切り文字を指定します (たとえば、単一引用符 (') を区切り記号として使用するための 2 つの単一引用符に置き換えるなど) のプリミティブな前処理します。 正確に (および場合)、スクリプト エンジン使用してこの情報は、スクリプト エンジンによって異なります。 このパラメーターに設定`NULL`ホストは、プロシージャの最後をマークする、区切り記号を使用しなかった場合。  
  
 `dwSourceContextCookie`  
 [in]デバッグのために使用するアプリケーション定義の値。  
  
 `ulStartingLineNumber`  
 [in]のどの行で文字列の解析を開始位置を指定するゼロベースの値。  
  
 `dwFlags`  
 [in]プロシージャに関連付けられるフラグ。 これらの値の組み合わせにすることができます。  
  
|定数|値|説明|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|示しますコード`pstrCode`プロシージャの戻り値を表す式を指定します。|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|示します、`this`ポインターが、プロシージャのスコープに含まれます。|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|示しますの親、`this`ポインターは、プロシージャのスコープに含まれています。|  
  
 `ppdisp`  
 [out]このメソッドによって解析されるプロシージャを既定の方法がここでは、ディスパッチ ラッパーを返します。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_NOTIMPL`|このメソッドはサポートされていません。 スクリプト エンジンは、名前空間をプロシージャの実行時の追加をサポートしていません。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンは未初期化または終了状態)。|  
|`OLESCRIPT_E_SYNTAX`|手順で指定されていない構文エラーが発生しました。|  
|`S_FALSE`|スクリプト エンジンがディスパッチ オブジェクト; をサポートしていません`ppdisp`にパラメーターが設定されている`NULL`です。|  
  
## <a name="remarks"></a>コメント  
 この呼び出し中には、スクリプト コードは評価されません。代わりに、プロシージャがコンパイル メソッドで`ppdisp`を呼び出すことができます、スクリプトによって後でします。  
  
 代わりにこのインターフェイスは推奨されません、`IActiveScriptParseProcedure`インターフェイスです。 `IActiveScriptParseProcedure::ParseProcedureText`メソッドは、このメソッドに似ていますが、プロシージャ名を指定することができます。 すべての状況で`IActiveScriptParseProcedure::ParseProcedureText`使用する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptParseProcedureOld インターフェイス](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)