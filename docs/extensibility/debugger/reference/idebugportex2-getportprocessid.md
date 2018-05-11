---
title: IDebugPortEx2::GetPortProcessId |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d41f01727ed5ee6a1db348da1c253120b1b13c2a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
ポート自体のプロセス ID を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetPortProcessId (   
   DWORD* pdwProcessId  
);  
```  
  
```csharp  
int GetPortProcessId (   
   out uint pdwProcessId  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdwProcessId`  
 [out]ポート自体の物理的なプロセス ID を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 Win32 ランタイムでなど、このメソッドは Win32 関数`GetCurrentProcessId`物理プロセス ID を取得するには  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)