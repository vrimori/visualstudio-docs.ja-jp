---
title: "IDebugApplication110::CallableWaitForHandles |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b259f5296f8e0b32def793a81e4c2e1069643306
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
シグナル状態になる一方で指定したハンドルのいずれかの待機スレッド間の呼び出しに、このスレッドに通知されます。 このメソッドは、デバッガー スレッドから呼び出す必要があります。  
  
> [!IMPORTANT]
>  [IDebugApplication110 インターフェイス](../../winscript/reference/idebugapplication110-interface.md)は、PDM v11.0 以降によって実装されている値を超えています。 activdbg100.h にあります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `handleCount`  
 待機ハンドルの数。  
  
 `pHandles`  
 待機ハンドルのセット。  
  
 `pIndex`  
 HRESULT 値が S_OK へのインデックス`pHandles`シグナル状態になったハンドル。  
  
## <a name="see-also"></a>関連項目  
 [IDebugApplication110 インターフェイス](../../winscript/reference/idebugapplication110-interface.md)