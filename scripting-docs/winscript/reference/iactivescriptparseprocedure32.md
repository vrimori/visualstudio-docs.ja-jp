---
title: IActiveScriptParseProcedure32 |Microsoft Docs
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
ms.openlocfilehash: 10cdff328216d06a3326dd3595ef8fc78bc9cfc9
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348114"
---
# <a name="iactivescriptparseprocedure32"></a>IActiveScriptParseProcedure32
実装して、Windows スクリプト エンジンでは、スクリプトに追加する手順については、ソース コードのテキストを許可している場合、`IActiveScriptParseProcedure32`インターフェイス。 これにより、解釈されたスクリプト言語 VBScript などの独立したオーサリング環境がないために別のメカニズム (以外の`IActiveScriptParse32`または`IPersist`*)、名前空間にスクリプトの手順を追加します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|||  
|-|-|  
|メソッド|説明|  
|[IActiveScriptParseProcedure32::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure32-parseproceduretext.md)|指定したコードのプロシージャを解析し、名前空間に、プロシージャを追加します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)