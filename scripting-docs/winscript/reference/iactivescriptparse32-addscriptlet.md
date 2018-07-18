---
title: IActiveScriptParse32::AddScriptlet |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fcf11eb2-8e71-4cca-afda-a91791c243ff
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 7b4ea62bf8afa4247fc7c4fdbea40c6b7c772661
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724552"
---
# <a name="iactivescriptparse32addscriptlet"></a>IActiveScriptParse32::AddScriptlet
コード スクリプトレットをスクリプトに追加します。 このメソッドは、スクリプトの永続状態が、ホスト ドキュメントに組み合わされたされ、ホストは、スクリプトを復元するため、環境で使用ではなくを通じて、`IPersist*`インターフェイスです。 プライマリの例としては、組み込みイベントにアタッチされている HTML ドキュメントに埋め込まれたコードのスクリプトレットを許可する HTML スクリプト言語 (たとえば、ONCLICK="button1.text='Exit'") です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrDefaultName`  
 [in]既定の名前に関連付けるスクリプトレットのアドレスです。 スクリプトレットに (上記の ONCLICK 例の場合) のように名前付けの情報が含まれていない場合、この名前はスクリプトレットを識別するために使用されます。 このパラメーターは、する場合`NULL`、必要に応じて、スクリプト エンジンが、一意の名前を製造します。  
  
 `pstrCode`  
 [in]追加するスクリプトレット テキストのアドレスです。 この文字列の解釈はスクリプト言語によって異なります。  
  
 `pstrItemName`  
 [in]このスクリプトレットに関連付けられている項目の名前を格納するバッファーのアドレスです。 このパラメーターは、だけでなく`pstrSubItemName`スクリプトレットのイベント ハンドラー オブジェクトを識別します。  
  
 `pstrSubItemName`  
 [in]名前を格納するバッファーのアドレス、`subobject`名前付きの項目をこのスクリプトレットが関連付けられている以外の場合は、名前付き項目の種類の情報でこの名前を検索するのです。 このパラメーターが NULL の代わりに名前付きアイテムと関連する場合は、スクリプトレット、`subitem`です。 さらに、このパラメーター`pstrItemName`スクリプトレットのイベント ハンドラーを特定のオブジェクトを識別します。  
  
 `pstrEventName`  
 [in]スクリプトレットは、イベント ハンドラーのイベントの名前を格納するバッファーのアドレスです。  
  
 `pstrDelimiter`  
 [入力] スクリプトレット末尾の区切り記号のアドレス。 ときに、`pstrCode`パラメーターは、テキストのストリームから解析は、ホストは、2 つの単一引用符 (")、スクリプトレットの末尾を検出するなど、通常、区切り文字を使用します。 このパラメーターには、ホストが使用する区切り文字を指定します。それにより、スクリプト エンジンで何らかの条件付きのプリミティブな前処理が可能になります (単一引用符 (') を区切り文字として使用するために 2 つの単一引用符に置き換えるなど)。 スクリプト エンジンがこの情報を厳密にどのような方法 (条件) で使用するかは、スクリプト エンジンによって異なります。 ホストがスクリプトレットの末尾を示すため、区切り記号を使用しなかった場合は、このパラメーターを NULL に設定します。  
  
 `dwSourceContextCookie`  
 [in]デバッグのために使用するアプリケーション定義の値。  
  
 `ulStartingLineNumber`  
 [入力] 解析が開始される行を指定するゼロから始まる値。  
  
 `dwFlags`  
 [入力] スクリプトレットに関連付けられるフラグ。 次の値の組み合わせが可能です。  
  
|戻り値|説明|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|スクリプト テキストをスクリプトの名前空間内でグローバル メソッドとして参照可能にする (名前で呼び出せるようにする) 必要があることを指定します。|  
|SCRIPTTEXT_ISPERSISTENT|スクリプト エンジンが保存される場合 (`IPersist*::Save` の呼び出しなどにより)、または初期化状態に戻すことでリセットされる場合、この呼び出し中に追加されたコードを保存する必要があることを指定します。 この状態の詳細については、スクリプト エンジンの状態を参照してください。|  
  
 `pbstrName` ,  
 [out]実際の名前がスクリプトレットを識別するために使用します。 これは、優先度の順にする: スクリプトレット テキストの名前を明示的に指定で提供される既定の名前`pstrDefaultName`、またはスクリプト エンジンが合成一意の名前。  
  
 `pexcepinfo` ,  
 [out]例外情報を含む構造体のアドレスです。 DISP_E_EXCEPTION を返す場合にこの構造体を入力する必要があります。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|スクリプトレットの解析中に例外が発生しました。 `pexcepinfo` パラメーターに例外に関する情報が格納されます。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_NOTIMPL`|このメソッドはサポートされていません。スクリプト エンジンでは、イベント シンク スクリプトレットの追加はサポートされていません。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれたまたは初期化) し、そのために失敗しました。|  
|`OLESCRIPT_E_INVALIDNAME`|このスクリプト言語で提供される既定の名前が正しくありません。|  
|`OLESCRIPT_E_SYNTAX`|指定されていない構文エラーがスクリプトレットで発生しました。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)