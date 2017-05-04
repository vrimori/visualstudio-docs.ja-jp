---
title: "IDebugDocumentHelper::Init | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Init
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Init"
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Init
`Init` のメソッドは、名前と最初の属性のデバッグのドキュメントのヘルパーを初期化します。  
  
## 構文  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### パラメーター  
 `pda`  
 \[出力\]このドキュメントに関連付けられたデバッグ アプリケーション。  
  
 `pszShortName`  
 \[入力\]ドキュメントの短い名前を含む文字列が null で終了します。  
  
 `pszLongName`  
 \[入力\]ドキュメントの長い名前を含む文字列が null で終了します。  
  
 `docAttr`  
 \[入力\]テキスト ドキュメントの属性を指定します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、名前と最初の属性のデバッグのドキュメントのヘルパーを初期化します。  
  
 このドキュメントでは、ツリー `IDebugDocumentHelper::Attach` が呼び出されるまで表示されません。  
  
## 参照  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper インターフェイス](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT\_DOC\_ATTR 定数](../../winscript/reference/text-doc-attr-constants.md)