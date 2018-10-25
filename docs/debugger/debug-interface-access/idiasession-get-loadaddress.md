---
title: Idiasession::get_loadaddress |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::get_loadAddress method
ms.assetid: 5162ae1a-38e3-4571-8995-4ed9be1dec3e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2de904777cf09e3289efae71bf585ece9c6444a8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49864297"
---
# <a name="idiasessiongetloadaddress"></a>IDiaSession::get_loadAddress
このシンボル ストア内のシンボルに対応する実行可能ファイルの読み込みアドレスを取得します。  
  
## <a name="syntax"></a>構文  
  
```C++  
HRESULT get_loadAddress (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pRetVal`  
 [out].Exe ファイルまたは .dll ファイルが読み込まれた仮想アドレス (VA) を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 返される読み込みアドレスは常に 0 しない限り、具体的には設定を使用して、 [idiasession::put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)メソッド。  
  
## <a name="see-also"></a>関連項目  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)