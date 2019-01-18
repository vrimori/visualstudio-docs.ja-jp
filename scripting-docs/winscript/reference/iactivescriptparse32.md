---
title: IActiveScriptParse32 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9f44239b4e423588b8455b93b87e4084a9c7d1c4
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347646"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Windows スクリプト エンジンをスクリプトに追加する未加工のテキスト コード スクリプトレットを許可またはにより、実行時に評価される式のテキストでは、実装されているか、`IActiveScriptParse32`インターフェイス。 これにより、解釈されたスクリプト言語 VBScript などの独立したオーサリング環境がないために別のメカニズム (以外の`IPersist*`)、スクリプト エンジンにスクリプト コードを取得して、さまざまなオブジェクトにスクリプトの断片をアタッチするにはイベント。  
  
## <a name="methods-in-vtable-order"></a>Vtable 順序のメソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|コード スクリプトレットをスクリプトに追加します。|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|スクリプト エンジンを初期化します。|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|名前空間に宣言を追加して、適切なコードを評価する、指定したコード スクリプトレットを解析します。|