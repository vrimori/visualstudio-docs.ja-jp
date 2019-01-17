---
title: IActiveScriptParseProcedureOld インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa7ea909680afdb65004f47e458d735e82ead929
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349995"
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld インターフェイス
スクリプトに追加する手順については、ソース コードのテキストを使用できます。 これにより、解釈されたスクリプト言語 VBScript などの独立系のオーサリング環境がないための代替手段 (以外の`IActiveScriptParse`または`IPersist*`) 名前空間にスクリプトの手順を追加します。  
  
> [!NOTE]
>  このインターフェイスが好評だったの非推奨とされます、`IActiveScriptParseProcedure`インターフェイス。  
  
## <a name="methods"></a>メソッド  
 継承されたメソッドだけでなく`IUnknown`、`IActiveScriptParseProcedureOld`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|指定したコードのプロシージャを解析し、名前空間、プロシージャを追加します。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)