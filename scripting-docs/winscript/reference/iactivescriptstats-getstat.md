---
title: IActiveScriptStats::GetStat |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d00c438f0fe03566dfb7efb93645cad02dc7477
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095395"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
スクリプトの標準的な統計情報のいずれかを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `stid`  
 [in]返される統計情報を指定します。 値にする必要があります。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|スクリプトの開始や、統計がリセットされた後に実行されるステートメントの数を返します。|  
  
 `pluHi`  
 [out]統計情報を表す 64 ビット符号なし整数の上位 32 ビット。  
  
 `pluLo`  
 [out]統計情報を表す 64 ビット符号なし整数の下位 32 ビット。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 使用可能な値などが、次の表の値に限定されません。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、スクリプトの標準的な統計情報のいずれかを返します。  
  
## <a name="see-also"></a>関連項目  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats インターフェイス](../../winscript/reference/iactivescriptstats-interface.md)