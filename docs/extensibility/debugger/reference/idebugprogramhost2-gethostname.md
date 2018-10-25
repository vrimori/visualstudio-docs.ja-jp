---
title: IDebugProgramHost2::GetHostName |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramHost2::GetHostName
helpviewer_keywords:
- IDebugProgramHost2::GetHostName
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d0e2ccf73ffdaa905585841eef99f84f59513867
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925207"
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
 [in]値、 [GETHOSTNAME_TYPE](../../../extensibility/debugger/reference/gethostname-type.md)列挙体。  
  
 `pbstrHostName`  
 [out]要求されたホスト プロセスの名前を返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、の一般的な実装で、`dwType`パラメーターは無視され、ホスト コンピューターのフレンドリ名が返されます。 もう 1 つの考えられる実装は、`dwType`への呼び出しにパラメーター、 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)メソッド名を取得します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)