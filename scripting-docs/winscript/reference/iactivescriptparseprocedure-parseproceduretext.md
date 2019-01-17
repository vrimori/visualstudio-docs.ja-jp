---
title: IActiveScriptParseProcedure::ParseProcedureText |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedure_ParseProcedureText
ms.assetid: 345a74ae-b4e8-42b2-abd8-633a370e8e7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ff49652897c106c1629d5f7b3133a66ccf7c981
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093406"
---
# <a name="iactivescriptparseprocedureparseproceduretext"></a>IActiveScriptParseProcedure::ParseProcedureText
指定したコードのプロシージャを解析し、名前空間、プロシージャを追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrCode`  
 [in]評価するプロシージャのテキストのアドレス。 この文字列の解釈はスクリプト言語によって異なります。  
  
 `pstrFormalParams`  
 [in]手順については、仮パラメーター名のアドレス。 パラメーター名は、スクリプト エンジンの適切な区切り記号で区切る必要があります。 名前をかっこで囲まれていない必要があります。  
  
 `pstrProcedureName`  
 [in]解析するプロシージャ名のアドレス。  
  
 `pstrItemName`  
 [in]プロシージャが評価されるコンテキストを与える項目名のアドレス。 このパラメーターは場合`NULL`コードは、スクリプト エンジンのグローバルなコンテキストで評価されます。  
  
 `punkContext`  
 [入力] コンテキスト オブジェクトのアドレス。 このオブジェクトはデバッグ環境用に予約されています。アクティブなランタイム コンテキストを表すためにデバッガーによって指定される場合があります。 このパラメーターは、する場合`NULL`、エンジンを使用して`pstrItemName`コンテキストを識別するためにします。  
  
 `pstrDelimiter`  
 [in]プロシージャの末尾の区切り記号のアドレス。 ときに`pstrCode`解析は、テキストのストリームからホスト通常を使用して、区切り記号、2 つの単一引用符 (")、プロシージャの終了を検出するなど。 このパラメーターには、ホストが使用する区切り文字を指定します。それにより、スクリプト エンジンで何らかの条件付きのプリミティブな前処理が可能になります (単一引用符 (') を区切り文字として使用するために 2 つの単一引用符に置き換えるなど)。 スクリプト エンジンがこの情報を厳密にどのような方法 (条件) で使用するかは、スクリプト エンジンによって異なります。 このパラメーターに設定`NULL`ホストでは、プロシージャの終わりをマークする、区切り記号を使用しなかった場合。  
  
 `dwSourceContextCookie`  
 [in]デバッグのために使用するアプリケーション定義の値。  
  
 `ulStartingLineNumber`  
 [入力] 解析が開始される行を指定するゼロから始まる値。  
  
 `dwFlags`  
 [in]プロシージャに関連付けられているフラグです。 次の値の組み合わせが可能です。  
  
|[値]|説明|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|示しますコードでは、`pstrCode`プロシージャの戻り値を表す式を指定します。 既定では、コードは、式、ステートメントの一覧、またはそれ以外の場合、スクリプト言語でプロシージャで許可されているものを含めることができます。|  
|SCRIPTPROC_IMPLICIT_THIS|示します、`this`ポインターは、プロシージャのスコープに含まれます。|  
|SCRIPTPROC_IMPLICIT_PARENTS|示しますの親、`this`ポインターは、プロシージャのスコープ内にあります。|  
  
 `ppdisp`  
 [out]スクリプトのグローバル メソッドとプロパティを含むオブジェクトのポインターのアドレス。 スクリプト エンジンは、このようなオブジェクトをサポートしていない場合`NULL`が返されます。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_NOTIMPL`|このメソッドはサポートされていません。 スクリプト エンジンは、名前空間には手順の実行時の追加をサポートしていません。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンは未初期化または終了状態)。|  
|`OLESCRIPT_E_SYNTAX`|手順で指定されていない構文エラーが発生しました。|  
|`S_FALSE`|スクリプト エンジンがディスパッチ オブジェクト; をサポートしていません`ppdisp`にパラメーターが設定されている`NULL`します。|  
  
## <a name="remarks"></a>Remarks  
 この呼び出し中にスクリプト コードは評価されません。代わりに、プロシージャは、呼び出すことができる、スクリプトによって後でスクリプトの状態にコンパイルされます。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)