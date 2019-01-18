---
title: SCRIPTGCTYPE 列挙型 |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b25ffb530bf16fff0008bb73b55ecb0c523efe0d
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349102"
---
# <a name="scriptgctype-enumeration"></a>SCRIPTGCTYPE 列挙型
実行するガベージ コレクションの型。 使用される、 [IActiveScriptGarbageCollector::CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>列挙値  
  
|||  
|-|-|  
|SCRIPTGCTYPE_NORMAL|通常のガベージ コレクションの操作を行います。 整数値は 0 です。|  
|SCRIPTGCTYPE_EXHAUSTIVE|完全なガベージ コレクションの操作を行います。 整数値には 1 です。|  
  
## <a name="see-also"></a>関連項目  
 [アクティブ スクリプトの定数、列挙型、およびエラー コード](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)