---
title: IActiveScript::AddNamedItem |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- AddNamedItem method, IActiveScript interface
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db65361e4bde14e803d9085a4530a505ccaf9fcb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642022"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
スクリプト エンジンの名前空間には、ルート レベルの項目の名前を追加します。 ルート レベルの項目は、プロパティとメソッド、イベント ソース、または 3 つすべてのオブジェクトです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrName`  
 [in]スクリプトから見た、アイテムの名前を格納するバッファーのアドレスです。 名前には、一意、持続可能なを指定する必要があります。  
  
 `dwFlags`  
 [in]アイテムに関連付けられるフラグ。 次の値の組み合わせが可能です。  
  
|値|説明|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|名前付きの項目がコード専用のオブジェクトを表すこと、およびホストなしを示す`IUnknown`にこのコードのみのオブジェクトに関連付けられます。 ホストでは、このオブジェクトの名前だけにします。 C などのオブジェクト指向言語でこのフラグはクラスを作成します。 すべての言語では、このフラグをサポートします。|  
|SCRIPTITEM_GLOBALMEMBERS|項目がグローバル プロパティと、スクリプトに関連付けられているメソッドのコレクションであることを示します。 スクリプト エンジンが、オブジェクト名を無視する通常、(他のよりのクッキーとして使用するために、 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)メソッド、または明示的なスコープを解決するため) グローバルとしては、そのメンバーを公開および変数とメソッド。 これにより、ホスト、ライブラリを拡張する (実行時の関数との) スクリプトに使用できます。 スクリプト エンジン名に対処するにはそのまま競合しています (たとえば、SCRIPTITEM_GLOBALMEMBERS の 2 つの項目では、同じ名前のメソッドがある) 場合、エラーは、このような状況により返されません必要があります。|  
|SCRIPTITEM_ISPERSISTENT|スクリプト エンジンが保存されている場合に、項目が保存されることを示します。 同様に、このフラグを設定することを示します初期化状態に戻す必要があります (スクリプト エンジン リリースする必要がある、ただし、実際のオブジェクト上のインターフェイスへのすべてのポインター)、項目の名前と種類の情報を維持することです。|  
|SCRIPTITEM_ISSOURCE|項目が、スクリプトをシンクするイベントを供給することを示します。 子オブジェクト (オブジェクトのプロパティ内にある自分のオブジェクト) には、イベント、スクリプトをソースもできます。 これは、再帰ではありませんが、一般的なケースを便利な機構など、コンテナーとそのメンバーのすべてのコントロールを作成します。|  
|SCRIPTITEM_ISVISIBLE|項目の名前が、プロパティ、メソッド、および項目のイベントへのアクセスを許可する、スクリプトの名前空間で使用できることを示します。 慣例により、項目のプロパティには、アイテムの子が含まれますそのため、すべての子オブジェクトのプロパティとメソッド (とその子を再帰的に) アクセスできなくなります。|  
|SCRIPTITEM_NOCODE|項目が対象のコードは関連付けられているべき項目として扱うことはできません、スクリプトの名前空間に追加される名前だけでは、ことを示します。 たとえば、フラグが設定されているこの、なし VBScript は、名前付き項目の個別のモジュールを作成および C++ は名前付きの項目の個別のラッパー クラスを作成する場合があります。|  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれたまたは初期化) します。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)