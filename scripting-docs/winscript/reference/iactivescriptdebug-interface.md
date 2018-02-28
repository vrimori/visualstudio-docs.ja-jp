---
title: "IActiveScriptDebug インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1e1d0c1cf51c63f1bb3fcd90ae72520da907e50
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebug-interface"></a>IActiveScriptDebug インターフェイス
デバッグをサポートするスクリプト エンジンによって実装されます。 通常を実装するオブジェクト、`IActiveScriptDebug`インターフェイスも実装して、`IActiveScript`インターフェイスです。 大文字と小文字の場合は、呼び出し、`IActiveScript::QueryInterface`を取得するメソッド、`IActiveScriptDebug`インターフェイスです。  
  
 `IActiveScriptDebug`インターフェイスにするための手段が用意されています。  
  
-   ドキュメントの管理を引き継ぐためのスマート ホストします。  
  
-   複数のスクリプト エンジンのデバッグを同期するためにプロセスのデバッグ マネージャーです。  
  
 継承されたメソッドだけでなく`IUnknown`、`IActiveScriptDebug`インターフェイスは、次のメソッドを公開します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|スクリプトのテキストの任意のブロックのテキスト属性を返します。|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|任意のスクリプトレットのテキスト属性を返します。|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|デリゲート`IDebugDocumentContext::EnumCodeContexts`です。|