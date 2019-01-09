---
title: Iactivescriptparse::initnew |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0998bea50d7839f93111aa6b116934fae35bfa3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089987"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
スクリプト エンジンを初期化します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>戻り値  
 返します`S_OK`成功した場合、または`E_FAIL`初期化中にエラーが発生した場合。  
  
## <a name="remarks"></a>Remarks  
 スクリプト エンジンを使用するには、次のいずれかのという必要があります: `IPersist*::Load`、 `IPersist*::InitNew`、または`IActiveScriptParse::InitNew`します。 このメソッドのセマンティクスは次のと同じ`IPersistStreamInit::InitNew`、ことで、このメソッド自体を初期化するためにスクリプト エンジンに指示します。 両方を呼び出すはしないことに注意してください。`IPersist*::InitNew`または`IActiveScriptParse::InitNew`と`IPersist*::Load`、もには、呼び出す`IPersist*::InitNew`、 `IActiveScriptParse::InitNew`、または`IPersist*::Load`2 回以上。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)