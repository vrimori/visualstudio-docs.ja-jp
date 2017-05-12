---
title: "IActiveScriptAuthor::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddNamedItem"
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# IActiveScriptAuthor::AddNamedItem
エンジンの名前空間を作成スクリプトにルート レベルの名前を追加します。  *ルート レベルの項目は*、プロパティおよびメソッドを含めることもイベント ソースを含むオブジェクトです。  
  
## 構文  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### パラメーター  
 `pszName`  
 \[入力\]スクリプトから表示される項目の名前。  名前は一意、永続なります。  
  
 `dwFlags`  
 \[出力\]名前付きの項目に関連付けられているフラグ。  次の値の組み合わせがあります:  
  
|定数|値|説明|  
|--------|-------|--------|  
|SCRIPTITEM\_ISVISIBLE|0x00000002|項目の名前がスクリプトの名前空間で使用できることを示します。  これは、項目のプロパティ、メソッド、およびイベントにアクセスできます。<br /><br /> 規則により、項目のプロパティは、項目の子メンバーが含まれます。  したがって、すべての子オブジェクトのプロパティとメソッド \(および子メンバー、再帰的\) にアクセスできます。|  
|SCRIPTITEM\_ISSOURCE|0x00000004|スクリプトは、スクリプト イベント ハンドラーを持つことができる項目のソースのイベントを示します。|  
|SCRIPTITEM\_GLOBALMEMBERS|0x00000008|項目がスクリプトに関連付けられたメソッドとグローバル プロパティのコレクションであることを示します。  このメンバーは、グローバル変数およびメソッドとして記述されます。|  
|SCRIPTITEM\_ISPERSISTENT|0x00000040|エンジンの作成スクリプトを保存する項目を保存することを示します。|  
|SCRIPTITEM\_CODEONLY|0x00000200|名前付きの項目のみがコード オブジェクトを表す、そのメンバーを作成する必要がないことを示します。|  
|SCRIPTITEM\_NOCODE|0x00000400|名前付きの項目が追加された名前だけである場合には、スクリプトを何もことを示します。|  
  
 `pdisp`  
 \[入力\]メソッド、プロパティ、またはイベント ソースの収集に使用される `NamedItem` のオブジェクトの `IDispatch`。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IActiveScriptAuthor インターフェイス](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)