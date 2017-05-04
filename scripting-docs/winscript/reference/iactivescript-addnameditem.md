---
title: "IActiveScript::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "AddNamedItem メソッド, IActiveScript インターフェイス"
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddNamedItem
スクリプト エンジンの名前空間にルート レベルの名前を追加します。  ルート レベルの項目はプロパティを持つオブジェクトとそのメソッド、イベント ソース、またはすべての 3 です。  
  
## 構文  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### パラメーター  
 `pstrName`  
 \[入力\]スクリプトで表示されるように、項目の名前を含むバッファーのアドレス。  名前は一意、永続なります。  
  
 `dwFlags`  
 \[入力\]フラグは、項目に関連付けられた  これらの値の組み合わせがあります:  
  
|値|説明|  
|-------|--------|  
|SCRIPTITEM\_CODEONLY|名前付きの項目にコードだけがオブジェクトを表すため、ホストには、このコードだけがオブジェクトに関連付ける `IUnknown` がないことを示します。  ホストがこのオブジェクトの名前のみがあります。  C\+\+ などのオブジェクト指向言語では、このフラグは、クラスを作成します。  一部の言語では、このフラグをサポートしていません。|  
|SCRIPTITEM\_GLOBALMEMBERS|項目がスクリプトに関連付けられたグローバル プロパティとメソッドのコレクションであることを示します。  通常、スクリプト エンジンは、オブジェクト名 \( [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) のメソッド、または明示的なスコープを解決するには、クッキーとして使用する以外\) は無視され、グローバル変数およびメソッドとしてメンバーを公開します。  これにより、ホストはスクリプトにランタイム ライブラリ \(関数など\) が拡張することができます。  エラーがこのような理由で返された状態必要ではありませんが、2 個の SCRIPTITEM\_GLOBALMEMBERS の項目に同じ名前のメソッドがある場合、スクリプト エンジンに名前の競合を処理します \(たとえば、\) をサポートします。|  
|SCRIPTITEM\_ISPERSISTENT|スクリプト エンジンを保存する項目を保存することを示します。  同様に、このフラグを設定すると、初期化された状態に戻る遷移は項目の名前と型情報を保持する必要があることを示します \(ただし、スクリプト エンジンが実際のオブジェクトのすべてのインターフェイスのポインターを解放する必要があります\)。|  
|SCRIPTITEM\_ISSOURCE|スクリプトをシンクすることができる項目のソースのイベント示します。  子オブジェクト \(オブジェクト自体がオブジェクトであるオブジェクトのプロパティは\) スクリプトにソース イベントもできます。  これは再帰的ではありませんが、コンテナーとメンバーのすべてのコントロールを作成する共通の例に便利な機構などを提供します。|  
|SCRIPTITEM\_ISVISIBLE|示し、アイテム名がスクリプトの名前空間で使用できることをプロパティへのアクセス、項目のメソッド、およびイベントができます。  規則では、項目のプロパティは、項目の子が含まれています; したがって、すべての子オブジェクトのプロパティとメソッド \(および子、再帰的\) にアクセスできます。|  
|SCRIPTITEM\_NOCODE|項目がスクリプトの名前空間に追加された名前だけでありコードが関連付けられている必要がある項目としてことを処理できません。  たとえば、設定されたこのフラグなしで VBScript は、名前付きの項目に対して別のモジュールを作成し、C\+\+ は、名前付きの項目に対して別のラッパー クラスを作成する場合があります。|  
  
## 戻り値  
 次の値の場合: 1  
  
|戻り値|説明|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引数が無効です。|  
|`E_POINTER`|無効なポインターが指定されました。|  
|`E_UNEXPECTED`|呼び出しが想定されていません \(たとえば、スクリプト エンジンはまだ読み込まれていないか、初期化されていません\)。|  
  
## 参照  
 [IActiveScript](../../winscript/reference/iactivescript.md)