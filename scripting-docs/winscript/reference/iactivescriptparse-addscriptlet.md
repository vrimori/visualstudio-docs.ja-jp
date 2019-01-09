---
title: Iactivescriptparse::addscriptlet |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b928efe2e8ac7bc0fbdb7c2ae9978a4418cbee7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090962"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
コード スクリプトレットをスクリプトに追加します。 このメソッドは、ホスト ドキュメントと絡まり合って、スクリプトの永続的な状態であり、ホストは、スクリプトを復元するため、環境で使用ではなくを通じて、`IPersist*`インターフェイス。 プライマリの例は、組み込みイベントにアタッチする HTML ドキュメントに埋め込まれたコードのスクリプトレットを許可する HTML のスクリプト言語 (たとえば、ONCLICK="button1.text='Exit'")。  
  
## <a name="syntax"></a>構文  
  
```cpp
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
 [in]既定の名前に、スクリプトレットを関連付けるのアドレス。 スクリプトレットに (上記の ONCLICK 例の場合) のように名前付けの情報が含まれていない場合、この名前は、スクリプトレットを識別するために使用されます。 このパラメーターが場合`NULL`、スクリプト エンジンは、必要な場合、一意の名前を製造しています。  
  
 `pstrCode`  
 [in]追加するスクリプトレット テキストのアドレス。 この文字列の解釈はスクリプト言語によって異なります。  
  
 `pstrItemName`  
 [in]このスクリプトレットに関連付けられている項目の名前を格納するバッファーのアドレス。 さらに、このパラメーター`pstrSubItemName`スクリプトレットがイベント ハンドラー オブジェクトを識別します。  
  
 `pstrSubItemName`  
 [in]名前を格納するバッファーのアドレスを`subobject`の名前付きの項目をこのスクリプトレットが関連付けられている;、名前付きの項目の種類の情報でこの名前を検索します。 スクリプトレットの代わりに名前付きの項目に関連する場合、このパラメーターが NULL、`subitem`します。 さらに、このパラメーター`pstrItemName`スクリプトレットがイベント ハンドラーを特定のオブジェクトを識別します。  
  
 `pstrEventName`  
 [in]スクリプトレットがイベント ハンドラーであるイベントの名前を格納するバッファーのアドレス。  
  
 `pstrDelimiter`  
 [入力] スクリプトレット末尾の区切り記号のアドレス。 ときに、`pstrCode`パラメーターがテキストのストリームから解析された、ホストは、2 つの単一引用符 (")、スクリプトレットの末尾を検出するなど、通常、区切り文字を使用します。 このパラメーターには、ホストが使用する区切り文字を指定します。それにより、スクリプト エンジンで何らかの条件付きのプリミティブな前処理が可能になります (単一引用符 (') を区切り文字として使用するために 2 つの単一引用符に置き換えるなど)。 スクリプト エンジンがこの情報を厳密にどのような方法 (条件) で使用するかは、スクリプト エンジンによって異なります。 ホストがスクリプトレットの末尾をマークする、区切り記号を使用しなかった場合は、このパラメーターを NULL に設定します。  
  
 `dwSourceContextCookie`  
 [in]デバッグのために使用するアプリケーション定義の値。  
  
 `ulStartingLineNumber`  
 [入力] 解析が開始される行を指定するゼロから始まる値。  
  
 `dwFlags`  
 [入力] スクリプトレットに関連付けられるフラグ。 次の値の組み合わせになります。  
  
|戻り値|説明|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|スクリプト テキストをスクリプトの名前空間内でグローバル メソッドとして参照可能にする (名前で呼び出せるようにする) 必要があることを指定します。|  
|SCRIPTTEXT_ISPERSISTENT|スクリプト エンジンが保存される場合 (`IPersist*::Save` の呼び出しなどにより)、または初期化状態に戻すことでリセットされる場合、この呼び出し中に追加されたコードを保存する必要があることを指定します。 この状態の詳細については、スクリプト エンジンの状態を参照してください。|  
  
 `pbstrName` ,  
 [out]スクリプトレットを識別するために使用される実際の名前。 これは、優先順位の順序であるため: スクリプトレット テキストでは、名前が明示的に指定で提供される既定の名前`pstrDefaultName`、またはスクリプト エンジンによって合成一意の名前。  
  
 `pexcepinfo` ,  
 [out]例外情報を格納する構造体のアドレス。 DISP_E_EXCEPTION が返された場合にこの構造体を入力する必要があります。  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`DISP_E_EXCEPTION`|スクリプトレットの解析中に例外が発生しました。 `pexcepinfo` パラメーターに例外に関する情報が格納されます。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_NOTIMPL`|このメソッドはサポートされていません。スクリプト エンジンでは、スクリプトレットのイベント シンクを追加することはできません。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれるまたは初期化) し、そのために失敗しました。|  
|`OLESCRIPT_E_INVALIDNAME`|このスクリプト言語で提供される既定の名前が正しくありません。|  
|`OLESCRIPT_E_SYNTAX`|指定されていない構文エラーがスクリプトレットで発生しました。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)