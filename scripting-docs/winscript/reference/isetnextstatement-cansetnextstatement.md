---
title: ISetNextStatement::CanSetNextStatement |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISetNextStatement.CanSetNextStatement
apilocation:
- scrobj.dll
ms.assetid: e2a54634-31ec-4d16-84e8-2b123845d876
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5288b0cffc3b8bfca0e995e67d4b3e4bf3a6b2e2
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54090130"
---
# <a name="isetnextstatementcansetnextstatement"></a>ISetNextStatement::CanSetNextStatement
このメソッドは、指定した場所にコードを実行するは、次のステートメントを決定するには、実行ポイントを設定できるかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT CanSetNextStatement(  
   IDebugStackFrame*  pStackFrame,  
   IDebugCodeContext*  pCodeContext  
)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pStackFrame`  
 [in]スタック フレーム オブジェクトへのポインター。  
  
 `pCodeContext`  
 [in]コードのコンテキスト オブジェクトへのポインター。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|次のステートメントは、指定したコードのコンテキストを更新できます。|  
|`S_FALSE`|次のステートメントは、指定したコードのコンテキストを更新できません。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [ISetNextStatement インターフェイス](../../winscript/reference/isetnextstatement-interface.md)