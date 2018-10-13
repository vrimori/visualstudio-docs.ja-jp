---
title: IDebugPortEx2::GetPortProcessId |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortEx2::GetPortProcessId
helpviewer_keywords:
- IDebugPortEx2::GetPortProcessId
ms.assetid: be85be66-47e6-415f-b0ca-24599aa5f13c
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c0843f6f33f55e427dabc4cce824fe3df0c89a1c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49260037"
---
# <a name="idebugportex2getportprocessid"></a>IDebugPortEx2::GetPortProcessId
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

ポート自体のプロセス ID を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 Win32 ランタイムでなど、このメソッドは Win32 関数`GetCurrentProcessId`物理プロセス ID を取得するには  
  
## <a name="see-also"></a>関連項目  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)

