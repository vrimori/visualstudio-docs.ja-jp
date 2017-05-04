---
title: "IScriptNode::CreateChildEntry | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode. CreateChildEntry
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildEntry"
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# IScriptNode::CreateChildEntry
`IScriptEntry`の子インスタンスを追加します。  
  
## 構文  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### パラメーター  
 `isn`  
 \[入力\]親の子のインデックス。  
  
 `dwCookie`  
 \[出力\]ホスト オブジェクトと子のエントリを関連付けるアプリケーション定義の値。  
  
 `pszDelimiter`  
 \[入力\]終わりのスクリプト ブロックの区切り記号のアドレス。  分析に対して、ホストでは、通常、スクリプト ブロックの末尾を検出するために、区切り記号 \(2 三つの単一引用符など\) を使用します。  
  
 区切り記号は、プリプロセスを提供するには、スクリプト エンジンを有効にします。  たとえば、エンジンは区切り記号として使用するために、2 種類の単一引用符で単一引用符を置き換える場合があります。  エンジンは区切り記号を使用する方法を指定します。  
  
 区切り記号がスクリプト ブロックの末尾が表示されない場合は NULL に設定します。  
  
 `ppse`  
 \[入力\]子のインスタンスの `IScriptEntry` のインターフェイスへのポインターを受け取る変数のアドレス。  
  
 Web ページを表す `IScriptNode` のオブジェクトの場合、このパラメーターはスクリプトのブロックを指定する `IScriptEntry` のインスタンス。  
  
 スクリプトのブロックを表します `IScriptEntry` のオブジェクトの場合、このパラメーターは関数オブジェクトを指定する `IScriptEntry` のインスタンス。  
  
 関数オブジェクトを表す `IScriptEntry` のオブジェクト、このメソッドは失敗します。  
  
 `IScriptScriptlet` のオブジェクト、このメソッドは失敗します。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 `IScriptNode` のインターフェイスは、Web ページまたは要素を表します。   \( `IScriptNode`から派生 `IScriptEntry` インターフェイスのスクリプト ブロックまたは関数オブジェクト表します。   \( `IScriptEntry`から派生 `IScriptScriptlet` インターフェイスのイベント ハンドラーを表します。  
  
## 参照  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)