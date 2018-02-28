---
title: "IActiveScriptParseProcedureOld インターフェイス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld interface
ms.assetid: d94b391e-4c24-46da-a01f-2c134ca4f041
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99cff9cd4d04c5d25489b6cc4c9b9af93792dc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptparseprocedureold-interface"></a>IActiveScriptParseProcedureOld インターフェイス
スクリプトに追加する手順については、ソース コードのテキストを使用できます。 これにより、VBScript などの独立した作成環境がない変換のスクリプト言語の代替手段 (以外の`IActiveScriptParse`または`IPersist*`) スクリプト プロシージャを名前空間に追加するのにします。  
  
> [!NOTE]
>  代わりにこのインターフェイスは推奨されません、`IActiveScriptParseProcedure`インターフェイスです。  
  
## <a name="methods"></a>メソッド  
 継承されたメソッドだけでなく`IUnknown`、`IActiveScriptParseProcedureOld`インターフェイスは、次のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptParseProcedureOld::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedureold-parseproceduretext.md)|指定したコードのプロシージャを解析し、プロシージャを名前空間に追加します。|  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptParseProcedure](../../winscript/reference/iactivescriptparseprocedure.md)