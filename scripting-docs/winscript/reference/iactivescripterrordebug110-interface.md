---
title: IActiveScriptErrorDebug110 インターフェイス |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110 Interface
ms.assetid: 5c1a4993-4cad-4ccf-89c2-53abfddfe1f2
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 067a62ec8b87c448577cfd6e5789ae5e073b5fb8
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345904"
---
# <a name="iactivescripterrordebug110-interface"></a>IActiveScriptErrorDebug110 インターフェイス
機能を追加、 [IActiveScriptDebug インターフェイス](../../winscript/reference/iactivescriptdebug-interface.md)します。 このインターフェイスは、BREAKREASON_ERROR イベントが発生した理由を確認するために JavaScript エンジンによって実装されます。  
  
> [!IMPORTANT]
>  このインターフェイスは、PDM v11.0 以降によって実装されます。 activdbg100.h にあります。  
  
## <a name="methods"></a>メソッド  
 `IActiveScriptErrorDebug110` インターフェイスは、以下のメソッドを公開します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md)|スローされた例外の種類を返します。|