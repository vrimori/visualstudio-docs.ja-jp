---
title: "IActiveScriptParse32 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 688a89515179912c1ed3ac815f0febf50ab4db0f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
かどうか、Windows スクリプト エンジンをスクリプトに追加される未加工のテキスト コード スクリプトレットを許可またはにより、実行時に評価される式のテキストを実装する、`IActiveScriptParse32`インターフェイスです。 これにより、VBScript などの独立したオーサリング環境がない変換のスクリプト言語は代替メカニズム (以外の`IPersist*`)、スクリプト エンジンには、スクリプト コードを取得して、さまざまなオブジェクトにスクリプト フラグメントをアタッチするにはイベントです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|コード スクリプトレットをスクリプトに追加します。|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|スクリプト エンジンを初期化します。|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|名前空間宣言を追加して、必要に応じてコードを評価する、指定したコード スクリプトレットを解析します。|