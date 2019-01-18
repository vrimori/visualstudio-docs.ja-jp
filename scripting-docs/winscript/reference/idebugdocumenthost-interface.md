---
title: IDebugDocumentHost インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46684bf2264813a8daaa466b98119496ba85d4b9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346541"
---
# <a name="idebugdocumenthost-interface"></a>IDebugDocumentHost インターフェイス
構文の色分け、デバッガーなどのホスト固有の機能を公開します。 `IDebugDocumentHelper::SetDebugDocumentHost`メソッドは引数としてこのインターフェイスを受け取ります。  
  
 継承されたメソッドだけでなく`IUnknown`、`IDebugDocumentHost`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|使用して追加された文字の範囲を返します`IDebugDocumentHelper::AddDeferredText`、元のホスト ドキュメント。|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|ドキュメントのテキストのブロックをテキスト属性を返します。|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|新しいドキュメント コンテキストが作成されると、により、必要に応じて、新しいコンテキストを制御するオブジェクトを取得するホストをホストに通知します。|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|ドキュメントのソース ファイルの完全なパス (ファイル名を含む) を返します。|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|パス情報がない場合、ドキュメントの名前を返します。|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|ドキュメントのソース ファイルが保存されていると、その内容を更新する必要があるホストに通知します。|