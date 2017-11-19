---
title: "IDebugDocumentHost インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adaeb98f18a052106036a91885696dd4b4760dea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthost-interface"></a>IDebugDocumentHost インターフェイス
構文の色分け、デバッガーをなどのホスト固有の機能を公開します。 `IDebugDocumentHelper::SetDebugDocumentHost`メソッドは引数としてこのインターフェイスを使用します。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugDocumentHost`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|使用して追加された文字の範囲を返します`IDebugDocumentHelper::AddDeferredText`、元のホスト ドキュメント。|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|ドキュメントのテキストのブロックのテキスト属性を返します。|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|新しいドキュメントのコンテキストは、作成し、ホスト オプションで新しいコンテキストを制御するオブジェクトを返すには、ホストに通知します。|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|ドキュメントのソース ファイルの完全パス (ファイル名を含む) を返します。|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|パス情報がない場合、ドキュメントの名前を返します。|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|ドキュメントのソース ファイルが保存されていると、その内容を更新する必要があるホストに通知します。|