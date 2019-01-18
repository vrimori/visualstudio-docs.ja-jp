---
title: IActiveScriptErrorDebug インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d773724d23c61aa72b8cd48917f2cd0bef4a7cb
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345202"
---
# <a name="iactivescripterrordebug-interface"></a>IActiveScriptErrorDebug インターフェイス
コンパイル時エラーとランタイム例外のドキュメントのコンテキスト情報を提供します。 `IActiveScriptError::QueryInterface`メソッドのサポート、`IActiveScriptErrorDebug`インターフェイス。  
  
 継承されたメソッドだけでなく`IActiveScriptError`、`IActiveScriptErrorDebug`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|このエラーは、ドキュメントのコンテキストを提供します。|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|ランタイム エラーを有効になっているスタック フレームを提供します。|