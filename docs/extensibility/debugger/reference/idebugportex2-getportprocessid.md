---
title: "IDebugPortEx2::GetPortProcessId |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortEx2::GetPortProcessId
helpviewer_keywords: IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 300f0553ee081dee8adc34ab48ce1989fc86e6c9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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