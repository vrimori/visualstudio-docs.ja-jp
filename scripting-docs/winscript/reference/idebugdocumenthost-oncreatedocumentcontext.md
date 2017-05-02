---
title: "IDebugDocumentHost::OnCreateDocumentContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.OnCreateDocumentContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::OnCreateDocumentContext"
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::OnCreateDocumentContext
新しいドキュメントのコンテキストが作成される通知し、ホストが必要に応じて新しいコンテキストの制御のワイルドカードを返すことをホストできます。  
  
## 構文  
  
```  
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### パラメーター  
 `ppunkOuter`  
 \[入力\]オブジェクトは、コントロール新しいコンテキスト。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_NOTIMPL`|ホストは、コントロール オブジェクトを提供しません。|  
  
## 解説  
 このメソッドは、ホストが指定されたヘルパー ドキュメントのコンテキストをに新しい機能を追加します。  このメソッドは、呼び出し元がコンテキストの作成を担当する **E\_NOTIMPL** または null の外部オブジェクトを返すことがあります。  
  
## 参照  
 [IDebugDocumentHost インターフェイス](../../winscript/reference/idebugdocumenthost-interface.md)