---
title: IActiveScriptParseProcedure32 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 387a856b-f5dc-4371-8620-bd574e046c2c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 8cd253db8cb63adad093b84c4bf47df07bd66d69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645872"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
実装する、Windows スクリプト エンジンでは、スクリプトに追加する手順については、ソース コードのテキストを許可している場合、`IActiveScriptParseProcedure32`インターフェイスです。 これにより、VBScript などの独立したオーサリング環境がない変換のスクリプト言語は代替メカニズム (以外の`IActiveScriptParse32`または`IPersist`*) スクリプト プロシージャを名前空間に追加するのにします。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|||  
|-|-|  
|メソッド|説明|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|指定したコードのプロシージャを解析し、名前空間に、プロシージャを追加します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)