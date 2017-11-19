---
title: "IActiveScriptSiteDebug32 インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: a752851aa6afd903747dc58fed79d2bc5b27e3e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 インターフェイス
スマート ホストの実装、`IActiveScriptSiteDebug32`インターフェイス ドキュメントの管理を実行して、デバッグに参加します。 `IActiveScriptSite`オブジェクトが通常の実装を提供、`IActiveScriptSiteDebug32`インターフェイスです。 これを行う場合、`IActiveScriptSite::QueryInterface`を取得するメソッド、`IActiveScriptSiteDebug32`インターフェイスです。  
  
 継承されたメソッドだけでなく`IUnknown`、`IActiveScriptSiteDebug32`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|このスクリプトのサイトに関連付けられているデバッグ アプリケーションのオブジェクトを返します。|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|デリゲートを言語エンジンで使用される`IDebugCodeContext::GetSourceContext`です。|