---
title: "IScriptNode::CreateChildHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.CreateChildHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildHandler"
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IScriptNode::CreateChildHandler
`IScriptNode`の子のインスタンスとしてスクリプトレットを追加します。  
  
## 構文  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### パラメーター  
 `pszDefaultName`  
 \[入力\]スクリプトレットに関連付ける既定の名前のアドレス。  
  
 `prgpszNames`  
 \[入力、size\_is \(`cpszNames`\) \] ホストの完全修飾名から ID の一覧。  
  
 `cpszNames`  
 \[入力\] `prgpszNames` のパラメーター識別子の数。  
  
 `pszEvent`  
 \[入力\]イベントの名前を識別するバッファーのアドレスは、スクリプトレットに関連付けられています。  
  
 `pszDelimiter`  
 \[入力\]終わりのスクリプト ブロックの区切り記号のアドレス。  分析に対して、ホストでは、通常、スクリプト ブロックの末尾を検出するために、区切り記号 \(2 三つの単一引用符など\) を使用します。  
  
 区切り記号はスクリプト エンジンを作成して、プリプロセスを有効にします。  たとえば、エンジンは区切り記号として使用するために、2 種類の単一引用符で単一引用符を置き換える場合があります。  エンジンは区切り記号を使用する方法を指定します。  
  
 スクリプト ブロックの末尾を識別するために区切り記号が使用されていない場合は無効にする。  
  
 `ptiSignature`  
 \[入力\]関数オブジェクトの型情報。  
  
 `iMethodSignature`  
 \[入力\] `ITypeInfo``ptiSignature` のパラメーター関数のインデックス。  
  
 `isn`  
 \[入力\]親の子のインデックス。  
  
 `dwCookie`  
 \[出力\]ホスト オブジェクトとエントリを関連付けるためのアプリケーション定義の値。  
  
 `ppse`  
 \[入力\]子のインスタンスの `IScriptEntry` のインターフェイスへのポインターを受け取る変数のアドレス。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 スクリプトレットは、イベント ハンドラーを指定します。  この方法は、Web ページを表す `IScriptNode` のオブジェクトで呼び出された場合スクリプトレットを作成します。  このメソッドは、他のインターフェイスで呼び出された場合、成功しません。  
  
## 参照  
 [IScriptNode インターフェイス](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)