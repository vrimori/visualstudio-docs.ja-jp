---
title: IActiveScriptParse |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0e3990ca43043909d99b309f58a344c1727450
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645832"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
かどうか、Windows スクリプト エンジンをスクリプトに追加される未加工のテキスト コード スクリプトレットを許可またはにより、実行時に評価される式のテキストを実装する、`IActiveScriptParse`インターフェイスです。 これにより、VBScript などの独立したオーサリング環境がない変換のスクリプト言語は代替メカニズム (以外の`IPersist*`)、スクリプト エンジンには、スクリプト コードを取得して、さまざまなオブジェクトにスクリプト フラグメントをアタッチするにはイベントです。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|スクリプト エンジンを初期化します。|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|コード スクリプトレットをスクリプトに追加します。|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|名前空間宣言を追加して、必要に応じてコードを評価する、指定したコード スクリプトレットを解析します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)