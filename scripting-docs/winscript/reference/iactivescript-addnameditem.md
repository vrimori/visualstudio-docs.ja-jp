---
title: Iactivescript::addnameditem |Microsoft Docs
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
ms.openlocfilehash: 4ae4a84821d0db226cbecb01e329e4f2941a675d
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095096"
---
# <a name="iactivescriptaddnameditem"></a>IActiveScript::AddNamedItem
スクリプト エンジンの名前空間には、ルート レベルの項目の名前を追加します。 ルート レベルの項目は、プロパティ、メソッド、イベント ソース、または 3 つすべてのオブジェクトです。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pstrName`  
 [in]スクリプトから参照すると、アイテムの名前を格納するバッファーのアドレス。 名前は、一意であり、永続化である必要があります。  
  
 `dwFlags`  
 [in]項目に関連付けられているフラグです。 次の値の組み合わせが可能です。  
  
|[値]|説明|  
|-----------|-------------|  
|SCRIPTITEM_CODEONLY|名前付きの項目が、コードのみのオブジェクトを表すことと、ホストでないことを示します`IUnknown`にこのコードのみのオブジェクトに関連付けられます。 ホストでは、このオブジェクトの名前だけにします。 C++ などのオブジェクト指向言語でこのフラグは、クラスを作成します。 すべての言語では、このフラグをサポートします。|  
|SCRIPTITEM_GLOBALMEMBERS|項目がコレクションのグローバル プロパティとメソッドがスクリプトに関連付けられていることを示します。 通常、スクリプト エンジンは、オブジェクト名を無視 (以外のクッキーとして使用するために、 [iactivescriptsite::getiteminfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)メソッド、または明示的なスコープを解決するため) とグローバルとしては、そのメンバーを公開変数とメソッド。 これにより、ライブラリを拡張する (実行時の関数と)、スクリプトで使用できるホストができます。 名前を処理するスクリプト エンジンに任されており (たとえば、2 つの SCRIPTITEM_GLOBALMEMBERS 項目では、同じ名前のメソッドがあります) 場合、競合が、エラーは、このような状況により返されないようにします。|  
|SCRIPTITEM_ISPERSISTENT|スクリプト エンジンが保存されている場合に、項目が保存されることを示します。 同様に、このフラグを設定することを示します初期化済み状態に遷移が (スクリプト エンジンで、する必要があります。 実際のオブジェクトのインターフェイスにすべてのポインターはリリースただし、)、項目の名前と型情報を保持する必要があります。|  
|SCRIPTITEM_ISSOURCE|項目が、スクリプトをシンクできるイベントをソースを示します。 子オブジェクト (オブジェクトのプロパティ、オブジェクト自体では) には、スクリプトにイベント ソースもできます。 これは、再帰ではありませんが、便利な機構を一般的なケースでは、たとえば、コンテナーとそのメンバーのすべてのコントロールを作成します。|  
|SCRIPTITEM_ISVISIBLE|項目の名前がプロパティ、メソッド、および項目のイベントにアクセスできるように、スクリプトの名前空間で使用できることを示します。 規則では、項目のプロパティには、アイテムの子にはが含まれます。そのため、すべての子オブジェクトのプロパティとメソッド (とその子では、再帰的に) にアクセスできます。|  
|SCRIPTITEM_NOCODE|項目が単純に、スクリプトの名前空間に追加される名は、対象のコードは関連付けられているはずの項目として扱うことはできないことを示します。 たとえば、このフラグが設定されていますが VBScript が名前付きの項目の個別のモジュールを作成し、C++ 名前付きの項目の個別のラッパー クラスを作成します。|  
  
## <a name="return-value"></a>戻り値  
 次のいずれかの値を返します。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが予期されていませんでした (たとえば、スクリプト エンジンがされていないされて読み込まれるまたは初期化) します。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScript](../../winscript/reference/iactivescript.md)