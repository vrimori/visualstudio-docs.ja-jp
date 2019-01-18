---
title: IActiveScriptParseProcedure |Microsoft Docs
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
ms.openlocfilehash: 78db05160adef51c414f4c4804f33d47812a9b38
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349544"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
実装して、Windows スクリプト エンジンでは、スクリプトに追加する手順については、ソース コードのテキストを許可している場合、`IActiveScriptParseProcedure`インターフェイス。 これにより、解釈されたスクリプト言語 VBScript などの独立したオーサリング環境がないために別のメカニズム (以外の`IActiveScriptParse`または`IPersist`*)、名前空間にスクリプトの手順を追加します。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|||  
|-|-|  
|メソッド|説明|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|指定したコードのプロシージャを解析し、名前空間に、プロシージャを追加します。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプト インターフェイス](../../winscript/reference/active-script-interfaces.md)