---
title: IActiveScriptSiteDebug インターフェイス |Microsoft Docs
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
ms.openlocfilehash: 339325686d2a98e34c6e9f96056612769a9e110e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348309"
---
# <a name="iactivescriptsitedebug-interface"></a>IActiveScriptSiteDebug インターフェイス
スマート ホストの実装、`IActiveScriptSiteDebug`ドキュメント管理を実行して、デバッグに参加するインターフェイス。 `IActiveScriptSite`オブジェクトは、通常の実装を提供します。、`IActiveScriptSiteDebug`インターフェイス。 この場合、呼び出し、`IActiveScriptSite::QueryInterface`メソッドを取得する、`IActiveScriptSiteDebug`インターフェイス。  
  
 継承されたメソッドだけでなく`IUnknown`、`IActiveScriptSiteDebug`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|委任に、言語エンジンによって使用される`IDebugCodeContext::GetSourceContext`します。|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|このスクリプトのサイトに関連付けられたデバッグ アプリケーション オブジェクトを返します。|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|スクリプト ドキュメントを追加する必要がありますアプリケーション ノードを取得します。|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|により、スマート ホストは実行時エラーを処理する方法を決定します。|