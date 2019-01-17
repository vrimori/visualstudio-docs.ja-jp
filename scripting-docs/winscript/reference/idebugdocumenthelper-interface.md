---
title: IDebugDocumentHelper インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHelper interface
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8fdb153a81d63a7a6cffd0b42001405ecfb87596
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346979"
---
# <a name="idebugdocumenthelper-interface"></a>IDebugDocumentHelper インターフェイス
などの多くにスマート ホストは、必要なインターフェイスの実装を提供、 `IDebugDocument`、 `IDebugDocumentContext`、 `IDebugDocumentProvider`、 `IDebugDocumentText`、および`IDebugDocumentTextEvents`インターフェイス。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugDocumentHelper`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|名前と初期属性でのデバッグ ドキュメント ヘルパーを初期化します。|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|ドキュメント ツリーには、このドキュメントを追加します。|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|ドキュメント ツリーから、このドキュメントを削除します。|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|終了する Unicode 文字列を追加します。 このドキュメントの。|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|DBCS を終了する文字列を追加します。 このドキュメントの。|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|セット、`IDebugDocumentHost`このドキュメントにします。|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|指定されたテキストは、使用可能な文字は提供されませんが、ヘルパーに通知します。|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|特定の範囲の文字が指定されたスクリプト エンジンによって処理されるスクリプト ブロック ヘルパーには、このことを示します。|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|スクリプト ブロックではない文字列に使用する既定の属性を設定します。|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|テキストの範囲で、属性を設定します。|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|ドキュメントの長い名前を設定します。|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|ドキュメントの短い名前を設定します。|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|このドキュメントの属性を設定します。|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|このドキュメントに対応するデバッグ アプリケーション ノードを返します。|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|文字とスクリプト ブロックに対応するスクリプト エンジンの範囲を取得します。|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|新しいデバッグ ドキュメントのコンテキストを作成します。|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|このドキュメントをユーザー インターフェイス、デバッガーの上部に表示されます。|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|このドキュメントのコンテキストをページのトップへデバッガー ユーザー インターフェイスに表示されます。|