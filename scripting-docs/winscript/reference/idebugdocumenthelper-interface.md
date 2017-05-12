---
title: "IDebugDocumentHelper インターフェイス | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentHelper インターフェイス"
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper インターフェイス
`IDebugDocument`、`IDebugDocumentContext`、`IDebugDocumentProvider`、`IDebugDocumentText`と `IDebugDocumentTextEvents` のインターフェイスなどのスマート ホストに、必要な追加のインターフェイスを実装します。  
  
 `IUnknown` から継承するメソッドに加え、`IDebugDocumentHelper` インターフェイスは次のメソッドを公開します。  
  
## Vtable 順序のメソッド  
  
|メソッド|説明|  
|----------|--------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|名前と最初の属性のデバッグのドキュメントのヘルパーを初期化します。|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|ドキュメント ツリーにこのドキュメントを追加します。|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|ドキュメント ツリーからこのドキュメントを削除します。|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|このドキュメントの末尾に Unicode 文字列を追加します。|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|このドキュメントの末尾に DBCS 文字列を追加します。|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|このドキュメントの `IDebugDocumentHost` を設定します。|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|指定したテキストとを使用できますが、文字はありません。ヘルパーに通知します。|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|文字の特定の範囲が特定のスクリプト エンジンによって処理されるスクリプト ブロックであることをヘルパーに示します。|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|既定の属性をスクリプト ブロックにないテキストに使用されるように設定します。|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|テキスト範囲の属性を設定します。|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|ドキュメントの長い名前を設定します。|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|ドキュメントの短い名前を設定します。|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|このドキュメントの属性を設定します。|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|このドキュメントに対応する、デバッグ アプリケーションのノードを返します。|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|スクリプト ブロックに対応する文字とスクリプト エンジンの範囲を取得します。|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|新しいデバッグのドキュメントのコンテキストを作成します。|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|デバッガーのユーザー インターフェイスの上部にこのドキュメントを提供します。|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|デバッガーのユーザー インターフェイスの上部にこのドキュメントのコンテキストを移動します。|