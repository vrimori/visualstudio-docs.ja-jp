---
title: IActiveScriptSiteDebug インターフェイス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9b36054deeceb0528fb7ea399cc41d8edbbb47e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724742"
---
# <a name="iactivescriptsitedebug-interface"></a>IActiveScriptSiteDebug インターフェイス
スマート ホストの実装、`IActiveScriptSiteDebug`インターフェイス ドキュメントの管理を実行して、デバッグに参加します。 `IActiveScriptSite`オブジェクトが通常の実装を提供、`IActiveScriptSiteDebug`インターフェイスです。 これを行う場合、`IActiveScriptSite::QueryInterface`を取得するメソッド、`IActiveScriptSiteDebug`インターフェイスです。  
  
 継承されたメソッドだけでなく`IUnknown`、`IActiveScriptSiteDebug`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|デリゲートを言語エンジンで使用される`IDebugCodeContext::GetSourceContext`です。|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|このスクリプトのサイトに関連付けられているデバッグ アプリケーションのオブジェクトを返します。|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|スクリプトでは、ドキュメントを追加するか、アプリケーション ノードを取得します。|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|により、スマート ホストは実行時エラーを処理する方法を決定します。|