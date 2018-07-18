---
title: Idiastackframe::get_rawlvarinstancevalue |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_rawLVarInstanceValue method
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2c50b1db74674158d4c7304bbacb4105f387cd56
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
ms.locfileid: "31466852"
---
# <a name="idiastackframegetrawlvarinstancevalue"></a>IDiaStackFrame::get_rawLVarInstanceValue
このメソッドは、実際のバイト数として指定されたローカル変数の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pInstance`  
 [in]`IDiaLVarInstance`ローカル変数の値を取得するのインスタンスを表すオブジェクト。  
  
 `cbDataMax`  
 [in]バッファー内のバイトの最大数を指す`pbData`です。 これは、8 バイトの最大数を指定できます (`sizeof(ULONGLONG)`)。  
  
 `pcbData`  
 [out]実際のバッファーに格納されるバイト数を返します。  
  
 `pbData`  
 [out]データを使用して入力バッファーです。 これは、ことはできません`NULL`です。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)