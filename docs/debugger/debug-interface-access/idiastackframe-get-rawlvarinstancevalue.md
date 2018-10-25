---
title: Idiastackframe::get_rawlvarinstancevalue |Microsoft Docs
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
ms.openlocfilehash: 7f5e34b766e27693326aba34b7b7259042870f00
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49933496"
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
 [in]`IDiaLVarInstance`の値を取得するローカル変数のインスタンスを表すオブジェクト。  
  
 `cbDataMax`  
 [in]バッファー内のバイトの最大数が指す`pbData`します。 これができる 8 バイトの最大値 (`sizeof(ULONGLONG)`)。  
  
 `pcbData`  
 [out]実際、バッファーに格納されるバイト数を返します。  
  
 `pbData`  
 [out]データと共に格納するバッファー。 これは `NULL` にすることはできません。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)