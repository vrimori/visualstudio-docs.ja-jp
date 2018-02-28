---
title: "IDebugProgramHost2::GetHostName |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 17cb56589f9f045b2f478626c47857d5c951494c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogramhost2gethostname"></a>IDebugProgramHost2::GetHostName
タイトル、フレンドリ名、またはこのプログラムのホスト プロセスのファイル名を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```csharp  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwType`  
 [in]値、 [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)列挙します。  
  
 `pbstrHostName`  
 [out]要求されたホスト プロセスの名前を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>コメント  
 このメソッドの一般的な実装で、`dwType`パラメーターは無視され、ホスト コンピューターのフレンドリ名が返されます。 渡すには、可能な別の実装、`dwType`パラメーターへの呼び出しに、 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)メソッド名を取得します。  
  
## <a name="see-also"></a>参照  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)