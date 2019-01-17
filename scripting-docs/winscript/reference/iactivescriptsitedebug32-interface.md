---
title: IActiveScriptSiteDebug32 インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03f42217-303d-46e7-9792-61a5ab95252c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e7937311e01274570e34bd639a0dc5f68206a3aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345566"
---
# <a name="iactivescriptsitedebug32-interface"></a>IActiveScriptSiteDebug32 インターフェイス
スマート ホストの実装、`IActiveScriptSiteDebug32`ドキュメント管理を実行して、デバッグに参加するインターフェイス。 `IActiveScriptSite`オブジェクトは、通常の実装を提供します。、`IActiveScriptSiteDebug32`インターフェイス。 この場合、呼び出し、`IActiveScriptSite::QueryInterface`メソッドを取得する、`IActiveScriptSiteDebug32`インターフェイス。  
  
 継承されたメソッドだけでなく`IUnknown`、`IActiveScriptSiteDebug32`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptSiteDebug32::GetApplication](../../winscript/reference/iactivescriptsitedebug32-getapplication.md)|このスクリプトのサイトに関連付けられたデバッグ アプリケーション オブジェクトを返します。|  
|[IActiveScriptSiteDebug32::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug32-getdocumentcontextfromposition.md)|委任に、言語エンジンによって使用される`IDebugCodeContext::GetSourceContext`します。|