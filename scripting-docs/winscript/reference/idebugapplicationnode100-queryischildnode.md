---
title: "IDebugApplicationNode100::QueryIsChildNode |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::QueryIsChildNode
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea31bbf4efbe6f47a3d2b7e97e001999fc692d7a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationnode100queryischildnode"></a>IDebugApplicationNode100::QueryIsChildNode
指定されたドキュメントがこのノードの子ノードのいずれかに属するかどうかを判断します。  
  
> [!IMPORTANT]
>  [IDebugApplicationNode100 インターフェイス](../../winscript/reference/idebugapplicationnode100-interface.md)は、PDM v10.0 によって実装される値を超えています。 activdbg100.h にあります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT QueryIsChildNode(        [in] IDebugDocument* pSearchKey        );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pSearchKey`  
 検索キー。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplicationNode100 インターフェイス](../../winscript/reference/idebugapplicationnode100-interface.md)