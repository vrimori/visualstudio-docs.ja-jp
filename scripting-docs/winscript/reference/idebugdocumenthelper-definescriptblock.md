---
title: "IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::DefineScriptBlock"
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::DefineScriptBlock
文字の特定の範囲が特定のスクリプト エンジンによって処理されるスクリプト ブロックであることをヘルパーに示します。  
  
## 構文  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### パラメーター  
 `ulCharOffset`  
 \[入力\]スクリプト ブロックの開始位置。  
  
 `cChars`  
 \[入力\]スクリプト ブロックの文字数。  
  
 `pas`  
 \[出力\]このスクリプト ブロックのスクリプト エンジン。  
  
 `fScriptlet`  
 \[入力\]フラグ。スクリプト ブロックがスクリプトレット示します。  
  
 `pdwSourceContext`  
 \[入力\]スクリプトのブロックのソースのコンテキスト。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 ホストは、スマート ドキュメントが埋め込まれたスクリプトのブロックを含める場合は、この方法を使用できます。  言語エンジンは、コードが他の言語の埋め込みスクリプトが含まれている場合は、この方法を使用できます。  
  
 スクリプト エンジンは、スクリプト ブロック内のすべての構文の色指定とコード コンテキストの検索に使用します。  
  
 `DefineScriptBlock` のメソッドは、テキストが追加された後に呼び出される必要があります \(たとえば、`IDebugDocumentHelper::AddDBCSText` のメソッドを使用\)、前にスクリプト ブロックが解析された \(たとえば、`IActiveScriptParse ::ParseScriptText` のメソッドを使用\)。  
  
## 参照  
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)