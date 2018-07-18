---
title: IActiveScriptParseProcedure |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77aaa60942855a71f7d71037fbefb06462336a13
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724382"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
実装する、Windows スクリプト エンジンでは、スクリプトに追加する手順については、ソース コードのテキストを許可している場合、`IActiveScriptParseProcedure`インターフェイスです。 これにより、VBScript などの独立したオーサリング環境がない変換のスクリプト言語は代替メカニズム (以外の`IActiveScriptParse`または`IPersist`*) スクリプト プロシージャを名前空間に追加するのにします。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|||  
|-|-|  
|メソッド|説明|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|指定したコードのプロシージャを解析し、名前空間に、プロシージャを追加します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)