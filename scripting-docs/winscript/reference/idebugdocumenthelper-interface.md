---
title: "IDebugDocumentHelper インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentHelper interface
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: baadcc1e2dba0b07e132298167b9b711e40cd912
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelper-interface"></a>IDebugDocumentHelper インターフェイス
スマート ホストに必要なインターフェイスの多くの実装を提供するように、 `IDebugDocument`、 `IDebugDocumentContext`、 `IDebugDocumentProvider`、 `IDebugDocumentText`、および`IDebugDocumentTextEvents`インターフェイスです。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugDocumentHelper`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|名前と最初の属性を持つデバッグ ドキュメント ヘルパーを初期化します。|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|このドキュメントをドキュメント ツリーに追加します。|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|このドキュメントをドキュメント ツリーから削除します。|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|終了する Unicode 文字列を追加、このドキュメントのです。|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|終了する DBCS 文字列を追加、このドキュメントのです。|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|セット、`IDebugDocumentHost`このドキュメントにします。|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|指定されたテキストが、利用できない文字は行われません、ヘルパーに通知します。|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|特定の範囲の文字は、指定されたスクリプト エンジンによって処理されるスクリプト ブロックのヘルパーを示します。|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|スクリプト ブロックに含まれていない文字列に使用する既定の属性を設定します。|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|テキストの範囲の属性を設定します。|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|ドキュメントの長い名前を設定します。|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|ドキュメントの短い名前を設定します。|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|このドキュメントの属性を設定します。|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|このドキュメントに対応するデバッグ アプリケーション ノードを返します。|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|文字と、スクリプト ブロックに対応するスクリプト エンジンの範囲を取得します。|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|新しいデバッグ ドキュメントのコンテキストを作成します。|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|ユーザー インターフェイスをデバッガーでは、最上位にこのドキュメントに表示されます。|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|このドキュメントのコンテキストをページのトップへデバッガー ユーザー インターフェイスに表示されます。|