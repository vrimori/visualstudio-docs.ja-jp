---
title: IActiveScriptParse32::InitNew |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 685c596caa61a5cbd5042fad3a1bfb39c349c1b1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094693"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32::InitNew
スクリプト エンジンを初期化します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_FAIL`初期化中にエラーが発生した場合。  
  
## <a name="remarks"></a>Remarks  
 スクリプト エンジンを使用するには、次のいずれかのという必要があります: `IPersist*::Load`、 `IPersist*::InitNew`、または`IActiveScriptParse32::InitNew`します。 このメソッドのセマンティクスは次のと同じ`IPersistStreamInit::InitNew`、ことで、このメソッド自体を初期化するためにスクリプト エンジンに指示します。 両方を呼び出すはしないことに注意してください。`IPersist*::InitNew`または`IActiveScriptParse32::InitNew`と`IPersist*::Load`、もには、呼び出す`IPersist*::InitNew`、 `IActiveScriptParse32::InitNew`、または`IPersist*::Load`2 回以上。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)