---
title: IScriptEntry::GetRange |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a4e053817ed4c503ebb41e2f3828da421e69ec7
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088739"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
開始位置とエントリの長さを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pichMin`  
 [out]`IScriptEntry`スクリプト ブロックを指定するオブジェクトは、0 を返します。  
  
 `IScriptEntry`関数オブジェクトを指定するオブジェクトが現在のスクリプト ブロックで、関数の開始位置を返します。  
  
 `IScriptScriptlet`オブジェクト、0 を返します。  
  
 `pcch`  
 [out]`IScriptEntry`スクリプト ブロックを指定するオブジェクトは、テキストの長さを返します。  
  
 `IScriptEntry`関数オブジェクトを指定するオブジェクトが関数定義の長さを返します。  
  
 `IScriptScriptlet`オブジェクト、エントリの長さを返します。  
  
## <a name="return-value"></a>戻り値  
 `HRESULT`。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>関連項目  
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)